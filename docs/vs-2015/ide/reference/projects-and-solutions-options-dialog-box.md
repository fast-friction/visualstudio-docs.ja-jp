﻿---
title: '[プロジェクトおよびソリューション] の [オプション] ダイアログ ボックス | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 245b453a3020e79b924cb8058ff392bd59673402
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662133"
---
# <a name="projects-and-solutions-options-dialog-box"></a>[プロジェクトおよびソリューション] の [オプション] ダイアログ ボックス
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] プロジェクト フォルダーの既定パスを設定し、プロジェクトの開発と構築に伴って、 **[出力]** ウィンドウ、 **[タスク一覧]** 、および **[ソリューション エクスプローラー]** の既定動作を決定します。 このダイアログ ボックスにアクセスするには、 **[ツール] メニューの [オプション]** をクリックして、 **[プロジェクトおよびソリューション]** を展開し、 **[全般]** をクリックします。

> [!NOTE]
> 使用している設定またはエディションによっては、ダイアログ ボックスで使用可能なオプションや、メニュー コマンドの名前や位置がヘルプに記載されている内容と異なる場合があります。 このヘルプ ページは、**全般的な開発設定**を考慮して記述されています。 設定を表示または変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。

## <a name="settings"></a>設定
 **プロジェクトの場所**新しいプロジェクトとソリューションのフォルダーとディレクトリが作成される既定の場所を設定します。 複数のダイアログ ボックスも、このオプションで指定した場所をフォルダーの開始点として使用します。 たとえば、[プロジェクトを開く] ダイアログ ボックスは、この場所を [マイ プロジェクト] のショートカットのために使用します。

 **ユーザープロジェクトテンプレートの場所** **[新しいプロジェクト]** ダイアログボックスで **[マイテンプレート**] の一覧を作成するために使用される既定の場所を設定します。 詳細については、「[方法 : プロジェクト テンプレートと項目テンプレートを配置して整理する](../../ide/how-to-locate-and-organize-project-and-item-templates.md)」を参照してください。

 **ユーザー項目テンプレートの場所** **[新しい項目の追加]** ダイアログボックスで **[マイテンプレート**] の一覧を作成するために使用される既定の場所を設定します。 詳細については、「[方法 : プロジェクト テンプレートと項目テンプレートを配置して整理する](../../ide/how-to-locate-and-organize-project-and-item-templates.md)」を参照してください。

 **ビルドがエラーで終了した場合は常にエラー一覧を表示する**プロジェクトのビルドに失敗した場合にのみ、ビルドの完了時に **[エラー一覧]** ウィンドウを開きます。 ビルド処理中に発生したエラーが表示されます。 このオプションがオフの場合、エラーは引き続き発生しますが、ビルドの完了時にウィンドウは開きません。 既定では、このオプションは有効になっています。

 **ソリューションエクスプローラーでアクティブな項目を追跡**するオンにすると、**ソリューションエクスプローラー**が自動的に開き、アクティブな項目が選択されます。 選択される項目は、プロジェクトまたはソリューション内の別のファイルや、デザイナー内の異なるコンポーネントを処理の対象にすると変更されます。 このオプションがオフのとき、**ソリューション エクスプローラー**での選択内容は自動的に変更されません。 既定では、このオプションは有効になっています。

 **ビルド構成の詳細を表示**選択すると、 **[プロジェクトのプロパティページ]** ダイアログボックスおよび **[ソリューションプロパティページ]** ダイアログボックスにビルド構成オプションが表示されます。 オフにすると、ビルドの構成オプションは、1 つの構成または 2 つの構成のデバッグとリリースを含む **および** プロジェクトのための、 **[プロジェクト プロパティ ページ]** ダイアログ ボックスや [[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]ソリューション プロパティ ページ[!INCLUDE[csprcs](../../includes/csprcs-md.md)]] ダイアログ ボックスに表示されません。 プロジェクトにユーザー定義の構成がある場合、ビルドの構成オプションが表示されます。

 オフの場合、 **[ビルド]** メニューのコマンド ( **[ソリューションのビルド]** 、 **[ソリューションのリビルド]** 、 **[ソリューションのクリーン]** など) はリリース構成で実行され、 **[デバッグ]** メニューのコマンド ( **[デバッグ開始]** 、 **[デバッグなしで開始]** など) はデバッグ構成で実行されます。

 **常にソリューションを表示する**この選択をオンにすると、ソリューションおよびソリューションで動作するすべてのコマンドが常に IDE に表示されます。 オフの場合、すべてのプロジェクトはスタンドアロン プロジェクトとして作成され、ソリューションに 1 つのプロジェクトだけが含まれている場合、ソリューション エクスプローラー内のソリューションや、IDE 内のソリューションで動作するコマンドは表示されません。

 **作成時に新しいプロジェクトを保存する**このチェックボックスをオンにすると、 **[新しいプロジェクト]** ダイアログボックスでプロジェクトの場所を指定できます。 オフの場合、すべての新しいプロジェクトは一時プロジェクトとして作成されます。 一時プロジェクトで作業する場合、ディスクの場所を指定しなくても、プロジェクトを作成して試してみることができます。

 **プロジェクトの場所が信頼されていない場合にユーザーに警告する**完全に信頼されていない場所 (UNC パスや HTTP パスなど) で、新しいプロジェクトを作成したり、既存のプロジェクトを開いたりすると、メッセージが表示されます。 このオプションを使用して、完全に信頼されていない場所でプロジェクトの作成またはオープンを試行するたびにメッセージを表示するかどうかを指定します。

 **ビルド開始時に出力ウィンドウを表示する**では、ソリューションビルドの初期段階で IDE に出力ウィンドウが自動的に表示されます。 詳細については、「[方法 : 出力ウィンドウを制御する](https://msdn.microsoft.com/library/91aebd15-8854-4a7a-9f7d-57376fb4e858)」を参照してください。 既定では、このオプションは有効になっています。

 **ファイル名の変更時にシンボルの名前変更を求めるプロンプトを表示する**このチェックボックスをオンにすると、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] プロジェクト内のすべての参照の名前をコード要素に変更するかどうかを確認するメッセージボックスが表示されます。

## <a name="see-also"></a>参照
 [[オプション] ダイアログ ボックス、[プロジェクトおよびソリューション]、[ビルド/実行]](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
