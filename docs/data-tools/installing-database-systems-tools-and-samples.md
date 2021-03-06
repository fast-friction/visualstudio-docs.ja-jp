---
title: データベースの互換性
ms.date: 09/06/2017
ms.topic: conceptual
helpviewer_keywords:
- database systems
- database compatibility
- databases for Visual Studio
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: cfc3b6c3adc5c51cbbc4bc7d91338fd3595ec372
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586407"
---
# <a name="compatible-database-systems-for-visual-studio"></a>Visual Studio 向けの互換性のあるデータベース システム

Visual Studio でデータ接続アプリケーションを開発するには、通常、データベースシステムをローカルの開発用コンピューターにインストールし、準備ができたらアプリケーションとデータベースを運用環境に配置します。 Visual Studio は、**データストレージと処理**ワークロードの一部としてコンピューターに LocalDB SQL Server Express インストールします。 この LocalDB インスタンスは、データ接続アプリケーションを迅速かつ簡単に開発するのに役立ちます。

データベースシステムを .NET アプリケーションからアクセスできるようにし、Visual Studio データツールウィンドウで表示できるようにするには、ADO.NET データプロバイダーが必要です。 .NET アプリケーションで Entity data model を使用する予定がある場合は、プロバイダーが Entity Framework をサポートする必要があります。 多くのプロバイダーは、NuGet パッケージマネージャーまたは Visual Studio Marketplace を通じて提供されます。

Azure storage Api を使用している場合は、運用環境にデプロイする準備が整うまで料金を避けるために、開発時にローカルコンピューターに Azure ストレージエミュレーターをインストールします。 詳細については、「[開発とテストのための Azure Storage Emulator の使用](/azure/storage/common/storage-use-emulator)」を参照してください。

次の一覧には、Visual Studio プロジェクトで使用できる一般的なデータベースシステムがいくつか含まれています。 この一覧は完全ではありません。 Visual Studio ツールとの緊密な統合を可能にする ADO.NET データプロバイダーを提供するサードパーティベンダーの一覧については、「 [ADO.NET Data providers](/dotnet/framework/data/adonet/data-providers)」を参照してください。

## <a name="microsoft-sql-server"></a>[Microsoft SQL Server]

SQL Server は、Microsoft の主要なデータベースオファリングです。 SQL Server 2016 は、画期的なパフォーマンス、高度なセキュリティ、豊富で統合されたレポートと分析を提供します。 さまざまなエディションに付属しています。これは、拡張性の高い高パフォーマンスのビジネス分析から、1台のコンピューターで使用できるように設計されています。 SQL Server Express は、再配布と埋め込み用に調整された SQL Server のフル機能エディションです。  LocalDB は SQL Server Express の簡略化されたエディションであり、構成を必要とせず、アプリケーションのプロセスで実行できます。 [SQL Server Express のダウンロードページ](https://www.microsoft.com/sql-server/sql-server-editions-express)から、または両方の製品をダウンロードできます。 このセクションの SQL の例の多くは、SQL Server LocalDB を使用しています。 SQL Server Management Studio (SSMS) は、Visual Studio SQL Server オブジェクトエクスプローラーで提供される機能よりも多くの機能を備えたスタンドアロンのデータベース管理アプリケーションです。 前のリンクから SSMS を取得できます。

## <a name="oracle"></a>Oracle

Oracle データベースの有料または無料のエディションは、 [oracle テクノロジのネットワーク](https://www.oracle.com/database/technologies/oracle-database-software-downloads.html)ページからダウンロードできます。 Entity Framework と Tableadapter のデザイン時サポートについては、 [Oracle Developer tools For Visual Studio](https://www.oracle.com/database/technologies/developer-tools/visual-studio/)が必要です。 Oracle インスタントクライアントを含むその他の公式 Oracle 製品は、NuGet パッケージマネージャーを通じて入手できます。 Oracle のサンプルスキーマは、 [oracle のオンラインドキュメント](https://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm)に記載されている手順に従ってダウンロードできます。

## <a name="mysql"></a>MySQL

MySQL は、企業や web サイトで広く使用されている、広く普及しているオープンソースのデータベースシステムです。 Mysql、mysql for Visual Studio、および関連製品のダウンロードは、 [Windows 上の mysql](https://www.mysql.com/why-mysql/windows/)にあります。 サードパーティは、さまざまな Visual Studio 拡張機能と、MySQL 用のスタンドアロン管理アプリケーションを提供します。 NuGet パッケージマネージャー ([**ツール** > **nuget パッケージマネージャー** > **ソリューションの nuget パッケージを管理**する]) でオファリングを参照できます。

## <a name="postgresql"></a>PostgreSQL

PostgreSQL は、オープンソースの無料のオブジェクトリレーショナルデータベースシステムです。 Windows にインストールするには、 [PostgreSQL のダウンロードページ](https://www.postgresql.org/download/windows/)からダウンロードできます。 また、ソースコードから PostgreSQL を構築することもできます。 PostgreSQL コアシステムには、C 言語インターフェイスが含まれています。 多くのサードパーティは、.NET アプリケーションから PostgreSQL を使用するための NuGet パッケージを提供しています。 NuGet パッケージマネージャー ([**ツール** > **nuget パッケージマネージャー** > **ソリューションの nuget パッケージを管理**する]) でオファリングを参照できます。 おそらく、最も一般的なパッケージは[npgsql.org](http://www.npgsql.org)によって提供されます。

## <a name="sqlite"></a>SQLite

SQLite は、アプリケーション独自のプロセスで実行される埋め込みの SQL データベースエンジンです。 これは、 [SQLite ダウンロードページ](https://www.sqlite.org/download.html)からダウンロードできます。 SQLite 用のサードパーティ製の NuGet パッケージも多数用意されています。 NuGet パッケージマネージャー ([**ツール** > **nuget パッケージマネージャー** > **ソリューションの nuget パッケージを管理**する]) でオファリングを参照できます。

## <a name="firebird"></a>Firebird

Firebird は、オープンソースの SQL データベースシステムです。 [Firebird ダウンロードページ](http://firebirdsql.org/en/downloads/)からダウンロードできます。 ADO.NET データプロバイダーは、NuGet パッケージマネージャーを通じて入手できます。

## <a name="see-also"></a>関連項目

- [Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)
- [SQL Server とそのコンポーネントのバージョンとエディションを確認する方法](https://support.microsoft.com/help/321185/how-to-determine-the-version-edition-and-update-level-of-sql-server-an)
