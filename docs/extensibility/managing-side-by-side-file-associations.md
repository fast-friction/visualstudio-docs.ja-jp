---
title: サイド バイ サイドでのファイルの関連付けの管理 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5d389ea97c9a77fe859a4029e4447adf76624e3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340663"
---
# <a name="manage-side-by-side-file-associations"></a>サイド バイ サイドでのファイルの関連付けを管理します。

サイド バイ サイドでインストールを処理する方法を決定する必要があります、VSPackage では、ファイルの関連付けを提供する場合の特定のバージョン[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ファイルを呼び出す必要があります。 互換性のないファイル形式は複合問題です。

ユーザーは、新しいバージョンのデータを失うことがなく、新しいバージョンで既存のファイルを読み込むことができるように、以前のバージョンと互換性がある製品を期待します。 理想的には、VSPackage 両方ロード、保存したり以前のバージョンのファイル形式。 になっていない場合は true は、ファイル形式を VSPackage の新しいバージョンにアップグレードを提供する必要があります。 このアプローチの欠点は、アップグレードされたファイルは、以前のバージョンで開くことができません。

この問題を回避するには、ファイル形式が互換性のないようになったときは、拡張機能を変更できます。 たとえば、VSPackage のバージョン 1 で、拡張機能を使用して *.mypkg10*とバージョン 2 は、拡張機能を使用できます *.mypkg20*します。 この違いは、特定のファイルを開き、VSPackage を識別します。 新しい Vspackage を古い拡張機能に関連付けられているプログラムの一覧に追加する場合に、ファイルを右クリックし、選択して新しい VSPackage で開きます。 その時点で、VSPackage は、ファイルを新しい形式にアップグレードまたはファイルを開くし、VSPackage の旧バージョンとの互換性を維持を提供できます。

> [!NOTE]
> これらのアプローチを組み合わせることができます。 たとえば、古いファイルを読み込んで、旧バージョンとの互換性を提供しをユーザーがそれを保存すると、ファイル形式をアップグレードできることできます。

## <a name="face-the-problem"></a>問題に直面します

バージョンを選択する必要があります、同じ拡張機能を使用する複数のサイド バイ サイドで Vspackage を実行する場合に、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]拡張機能に関連付けられています。 2 つの方法を次に示します。

- 最新バージョンのファイルを開く[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ユーザーのコンピューターにインストールされています。

   この方法では、インストーラーがの最新バージョンを判断する[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ファイルの関連付け用に記述されたレジストリ エントリでそれを含めるとします。 Windows インストーラー パッケージの最新バージョンを示すプロパティを設定するカスタム アクションを含めることができます[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。

  > [!NOTE]
  > このコンテキストで「最新」意味「最新のサポート バージョン」 これらのエントリをインストーラーがの今後のリリースを自動的に検出されない[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。 内のエントリ[システム要件の検出](../extensibility/internals/detecting-system-requirements.md)し[コマンドをする必要がありますが実行後にインストール](../extensibility/internals/commands-that-must-be-run-after-installation.md)はここで示されたに似ており、その他のバージョンのサポートに必要な[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。

   CustomAction テーブル内の次の行が、AppSearch によって設定されたプロパティを DEVENV_EXE_LATEST プロパティを設定し、で説明した RegLocator テーブル[インストール後に実行する必要がありますコマンド](../extensibility/internals/commands-that-must-be-run-after-installation.md)します。 InstallExecuteSequence テーブル内の行では、実行シーケンスの早い段階でカスタム アクションをスケジュールします。 条件列 make ロジック作業の値:

  - Visual Studio .NET 2002 は、のみに存在するバージョンである場合、最新バージョンです。

  - 存在する場合にのみ、visual Studio .NET 2003 は、最新のバージョンと[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]が存在しません。

  - [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 存在のみのバージョンである場合、最新バージョンです。

    最終的な結果は、DEVENV_EXE_LATEST に最新バージョンの devenv.exe のパスが含まれています。

  **Visual Studio の最新バージョンを決定する CustomAction テーブル行**

  |アクション|型|ソース|ターゲット|
  |------------|----------|------------|------------|
  |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|
  |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|
  |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|

  **Visual Studio の最新バージョンを決定する InstallExecuteSequence テーブル行**

  |アクション|条件|シーケンス|
  |------------|---------------|--------------|
  |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 および NOT (DEVENV_EXE_2003 または DEVENV_EXE_2005)|410|
  |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 と DEVENV_EXE_2005 されません。|420|
  |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|

   Windows インストーラー パッケージのレジストリのテーブルに書き込む DEVENV_EXE_LATEST プロパティを使用することができます、 **HKEY_CLASSES_ROOT*ProgId*ShellOpenCommand**キーの既定値、[DEVENV_EXE_LATEST]"%1"

- 使用可能な VSPackage のバージョンから最適な選択が可能な共有ランチャー プログラムを実行します。

   開発者[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ソリューションおよびプロジェクトの多くのバージョンから作成されるは、複数の形式の複雑な要件を処理するには、このアプローチにした[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。 この方法では、ランチャー プログラムを拡張機能ハンドラーとして登録します。 ランチャーがファイルをチェックしのバージョンを決定[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSPackage は、その特定のファイルを処理できます。 たとえば場合、VSPackage の特定のバージョンで最後に保存されているファイルを開くと、ランチャーで起動できますその VSPackage の一致するバージョン[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。 さらに、ユーザーは、常に最新のバージョンを開始する起動ツールを構成する可能性があります。 起動ツールは、ファイルの形式にアップグレードするユーザーも要求でした。 ファイルの形式には、バージョン番号が含まれている場合、ランチャーは、ファイル形式は、1 つ以上インストールされている Vspackage のより後のバージョンの場合、ユーザーに通知する可能性があります。

   ランチャーは、VSPackage のすべてのバージョンと共有されている Windows インストーラー コンポーネントでなければなりません。 このプロセスにより、最新のバージョンが常にインストールされているし、VSPackage のすべてのバージョンがアンインストールされるまでは削除されません。 これにより、ファイルの関連付けとランチャ コンポーネントの他のレジストリ エントリは保持される場合でも、VSPackage の 1 つのバージョンがアンインストールされます。

## <a name="uninstall-and-file-associations"></a>アンインストールして、ファイルの関連付け

ファイルの関連付けのレジストリ エントリを書き込む VSPackage のアンインストールには、ファイルの関連付けが削除されます。 したがって、拡張機能では、関連付けられているプログラムはありません。 Windows インストーラーはありません"recover"、VSPackage のインストール時に追加されたレジストリ エントリ。 ユーザーのファイルの関連付けを修正する方法を次に示します。

- 前述のような共有ランチャー コンポーネントを使用します。

- ユーザーがファイルの関連付けを所有する VSPackage のバージョンの修復を実行するように指示します。

- 適切なレジストリ エントリをリライトする独立した実行可能プログラムを提供します。

- ユーザーがファイルの関連付けを選択し、失われた関連付けを再利用できる構成オプションのページまたはダイアログ ボックスを提供します。 アンインストール後に実行するユーザーに指示します。

## <a name="see-also"></a>関連項目

- [サイド バイ サイドで配置のファイル名拡張子を登録します。](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [ファイル名拡張子の動詞を登録します。](../extensibility/registering-verbs-for-file-name-extensions.md)