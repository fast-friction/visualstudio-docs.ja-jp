---
title: 'チュートリアル: トランザクションにデータを保存する'
ms.date: 09/08/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c0efdda51a52b18697828e1772eb4a71435753e8
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586238"
---
# <a name="walkthrough-save-data-in-a-transaction"></a>チュートリアル: トランザクションにデータを保存する

このチュートリアルでは、<xref:System.Transactions> 名前空間を使用してトランザクションにデータを保存する方法について説明します。 このチュートリアルでは、Windows フォームアプリケーションを作成します。 データソース構成ウィザードを使用して、Northwind サンプルデータベースに2つのテーブルのデータセットを作成します。 データバインドコントロールを Windows フォームに追加し、BindingNavigator の [保存] ボタンのコードを変更して、TransactionScope 内のデータベースを更新します。

## <a name="prerequisites"></a>Prerequisites

このチュートリアルでは SQL Server Express LocalDB と Northwind サンプルデータベースを使用します。

1. LocalDB SQL Server Express ない場合は、 [SQL Server Express ダウンロードページ](https://www.microsoft.com/sql-server/sql-server-editions-express)からインストールするか、 **Visual Studio インストーラー**を使用してインストールします。 Visual Studio インストーラーでは、SQL Server Express LocalDB を **.net デスクトップ開発**ワークロードの一部としてインストールすることも、個々のコンポーネントとしてインストールすることもできます。

2. 次の手順に従って、Northwind サンプルデータベースをインストールします。

    1. Visual Studio で、 **[SQL Server オブジェクトエクスプローラー]** ウィンドウを開きます。 (SQL Server オブジェクトエクスプローラーは、Visual Studio インストーラーの**データストレージと処理**ワークロードの一部としてインストールされます)。 **[SQL Server]** ノードを展開します。 LocalDB インスタンスを右クリックし、 **[新しいクエリ]** をクリックします。

       クエリエディターウィンドウが開きます。

    2. [Northwind transact-sql スクリプト](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)をクリップボードにコピーします。 この T-sql スクリプトでは、Northwind データベースを最初から作成し、データを設定します。

    3. T-sql スクリプトをクエリエディターに貼り付け、 **[実行]** ボタンをクリックします。

       しばらくすると、クエリの実行が完了し、Northwind データベースが作成されます。

## <a name="create-a-windows-forms-application"></a>Windows フォーム アプリケーションを作成する

最初の手順では、 **Windows フォームアプリケーション**を作成します。

1. Visual Studio の **[ファイル]** メニューで､ **[新規作成]**  >  **[プロジェクト]** を選択します。

2. 左側のウィンドウで、**ビジュアルC#** または**Visual Basic**を展開し、 **[Windows デスクトップ]** を選択します。

3. 中央のウィンドウで、 **[Windows フォーム App]** プロジェクトの種類を選択します。

4. プロジェクトに**SavingDataInATransactionWalkthrough**という名前を入力し、[ **OK]** をクリックします。

     **SavingDataInATransactionWalkthrough** プロジェクトが作成されて**ソリューション エクスプローラー**に追加されます。

## <a name="create-a-database-data-source"></a>データベースデータソースの作成

この手順では、**データソース構成ウィザード**を使用して、Northwind サンプルデータベースの `Customers` テーブルと `Orders` テーブルに基づいてデータソースを作成します。

1. データ **[ソース]** ウィンドウを開くには、 **[データ]** メニューの **[データソースの表示]** をクリックします。

2. **[データ ソース]** ウィンドウで、 **[新しいデータ ソースの追加]** をクリックして**データ ソース構成ウィザード**を起動します。

3. **[データソースの種類を選択]** 画面で、 **[データベース]** を選択し、 **[次へ]** を選択します。

4. **[データ接続の選択]** 画面で、次のいずれかの操作を行います。

    - Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は選択します。

         -または-

    - **[新しい接続]** を選択して **[接続の追加] または [接続の変更]** ダイアログ ボックスを表示し、Northwind データベースへの接続を作成します。

5. データベースにパスワードが必要な場合は、機密データを含めるオプションを選択し、 **[次へ]** を選択します。

6. **[アプリケーション構成ファイルへの接続文字列の保存]** 画面で、 **[次へ]** を選択します。

7. **[データベースオブジェクトの選択]** 画面で、 **[テーブル]** ノードを展開します。

8. `Customers` テーブルと `Orders` テーブルを選択し、 **[完了]** を選択します。

     プロジェクトに **NorthwindDataSet** が追加され、 **[データ ソース]** ウィンドウに `Customers` テーブルと `Orders` テーブルが表示されます。

## <a name="add-controls-to-the-form"></a>フォームへのコントロールの追加

**[データ ソース]** ウィンドウからフォームに項目をドラッグして、データ バインド コントロールを作成します。

1. **[データソース]** ウィンドウで、 **[Customers]** ノードを展開します。

2. **[データ ソース]** ウィンドウから **Form1** にメインの **[Customers]** ノードをドラッグします。

   レコード間をナビゲートするための <xref:System.Windows.Forms.DataGridView> コントロールとツール ストリップ (<xref:System.Windows.Forms.BindingNavigator>) がフォームに表示されます。 コンポーネントトレイに、 [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、`CustomersTableAdapter`、<xref:System.Windows.Forms.BindingSource>、および <xref:System.Windows.Forms.BindingNavigator> が表示されます。

3. 関連する **orders** ノード (メインの **orders** ノードではなく、**Fax** 列の下にある 関連する子テーブル ノード) を、顧客 の  **datagridview** の下のフォームにドラッグします。

   <xref:System.Windows.Forms.DataGridView> がフォームに表示されます。 コンポーネントトレイに `OrdersTableAdapter` と <xref:System.Windows.Forms.BindingSource> が表示されます。

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>System.string アセンブリへの参照を追加します。

トランザクションは、<xref:System.Transactions> 名前空間を使用します。 System.Transactions アセンブリへのプロジェクト参照は既定で追加されないため、手動で追加する必要があります。

### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>System.Transactions の DLL ファイルへの参照を追加するには

1. **[プロジェクト]** メニューの **[参照の追加]** を選択します。

2. **[.Net]** タブで [ **system.string] を選択し**、[ **OK]** を選択します。

     **System.Transactions** への参照がプロジェクトに追加されます。

## <a name="modify-the-code-in-the-bindingnavigators-saveitem-button"></a>BindingNavigator の SaveItem ボタンのコードを変更する

フォームに最初にドロップされたテーブルに対して、既定では、<xref:System.Windows.Forms.BindingNavigator>の [保存] ボタンの `click` イベントにコードが追加されます。 追加テーブルを更新する場合は、手動でコードを追加する必要があります。 このチュートリアルでは、[保存] ボタンのクリックイベントハンドラーから既存の保存コードをリファクターします。 また、行を追加または削除する必要があるかどうかに基づいて、特定の更新機能を提供するためのメソッドもいくつか作成します。

### <a name="to-modify-the-auto-generated-save-code"></a>自動生成された保存コードを変更するには

1. **顧客 Sbindingnavigator**の **[保存]** ボタン (フロッピーディスクのアイコンが付いたボタン) を選択します。

2. `CustomersBindingNavigatorSaveItem_Click` メソッドを次のコードで置き換えます。

     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]

関連するデータへの変更を解決する順序は次のとおりです。

- 子レコードを削除します。 (この場合は、`Orders` テーブルからレコードを削除します)。

- 親レコードを削除します。 (この場合は、`Customers` テーブルからレコードを削除します)。

- 親レコードを挿入します。 (この例では、`Customers` テーブルにレコードを挿入します)。

- 子レコードを挿入します。 (この例では、`Orders` テーブルにレコードを挿入します)。

### <a name="to-delete-existing-orders"></a>既存の注文を削除するには

- 次の `DeleteOrders` メソッドを **Form1** に追加します。

     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-csharp[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]

### <a name="to-delete-existing-customers"></a>既存の顧客を削除するには

- 次の `DeleteCustomers` メソッドを **Form1** に追加します。

     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-csharp[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]

### <a name="to-add-new-customers"></a>新規顧客を追加するには

- 次の `AddNewCustomers` メソッドを **Form1** に追加します。

     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-csharp[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]

### <a name="to-add-new-orders"></a>新規注文を追加するには

- 次の `AddNewOrders` メソッドを **Form1** に追加します。

     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-csharp[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]

## <a name="run-the-application"></a>アプリケーションの実行

**F5** キーを押してアプリケーションを実行します。

## <a name="see-also"></a>関連項目

- [方法 : トランザクションを使用してデータを保存する](../data-tools/save-data-by-using-a-transaction.md)
- [データをデータベースに保存する](../data-tools/save-data-back-to-the-database.md)
