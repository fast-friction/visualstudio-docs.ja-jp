---
title: Visual Studio のツール for Office runtime のインストール シナリオ
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, installation scenarios
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 507bce496405f615343a9c109ff71196d814af08
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438740"
---
# <a name="visual-studio-tools-for-office-runtime-installation-scenarios"></a>Visual Studio のツール for Office runtime のインストール シナリオ
  3 つの方法で、Visual Studio 2010 Tools for Office ランタイムをインストールすることができます。

- Visual Studio のインストール時。

- Microsoft Office のインストール時。

- Visual Studio 2010 Tools for Office ランタイム再頒布可能パッケージをインストールするとします。

  インストールされるランタイム コンポーネントは、コンピューターの構成およびインストール シナリオによって異なります。

## <a name="runtime-components-that-are-installed-in-each-installation-scenario"></a>各インストール シナリオでインストールされているランタイム コンポーネント
 Visual Studio 2010 Tools for Office ランタイムが 3 つのコンポーネント: Office ソリューション ローダー、.NET Framework 3.5 の Office 拡張機能および用の Office 拡張機能、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]またはそれ以降。 ランタイムをインストールすると、常に Office ソリューション ローダーがインストールされます。 .NET Framework 用の Office 拡張機能のインストールは、コンピューターの構成およびインストール シナリオによって異なります。 最初にランタイムをインストールするときにどちらかの Office 拡張機能をインストールできない場合、後で特定の要件を満たすと、インストールされていない Office 拡張機能がランタイムによって自動的にインストールされます。 ランタイムのこの機能は呼*オンデマンド インストール*します。

 各ランタイム インストールのシナリオで、既定でインストールされるランタイム コンポーネントを次の表に示します。 各シナリオの詳細については、後で説明します。

|ランタイムのインストール シナリオ|Office ソリューション ローダー|.NET Framework 3.5 用の Office 拡張機能|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] の Office 拡張機能|[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] の Office 拡張機能|
|-----------------------------------|----------------------------|--------------------------------------------------| - |---------------------------------------------------------------------------|
|[!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] 以降を使用する場合|はい|○ (.NET Framework Version 3.5 がインストール済みの場合)|はい|はい|
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] を使用する場合|はい|○ (.NET Framework Version 3.5 がインストール済みの場合)|いいえ|いいえ|
|Office 2010 Service Pack 1 (SP1) 以降を使用する場合|はい|○ (.NET Framework Version 3.5 がインストール済みの場合)|○ ([!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] がインストール済みの場合)|いいえ|
|ランタイムの再頒布可能パッケージのインストール時|はい|○ (.NET Framework Version 3.5 がインストール済みの場合)|○ ([!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] がインストール済みの場合)|○ ([!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] がインストール済みの場合)|

### <a name="install-the-runtime-with-visual-studio-or-the-microsoft-office-developer-tools-for-visual-studio"></a>Visual Studio または Microsoft Office Developer Tools for Visual Studio のランタイムをインストールします。
 Visual Studio の Office Developer Tools をインストールすると、開発用コンピューターに [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] および [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 用の Office 拡張機能が常にインストールされます。 また、.NET Framework 3.5 用の Office 拡張機能は、開発用コンピューターに .NET Framework 3.5 が既に存在している場合にのみインストールされます。 [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] をインストールした後で .NET Framework 3.5 をインストールすると、初めて .NET Framework 3.5 を対象とする Office プロジェクトを作成するときに、.NET Framework 3.5 用の Office 拡張機能がランタイムによって自動的にインストールされます。

> [!WARNING]
> [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] 以降を使用して .NET Framework 3.5 を対象とする Office プロジェクトを作成することはできません。

 Office developer tools をインストールする方法の詳細については、次を参照してください。[方法。Office ソリューションを開発するコンピューターを構成する方法](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)」を参照してください。

### <a name="install-the-runtime-with-office"></a>Office ランタイムをインストールします。
 コンピューターに .NET Framework 3.5 が既に存在している場合、Office をインストールすると、.NET Framework 3.5 用の Office 拡張機能がインストールされます。 Office の後で .NET Framework 3.5 をインストールすると、初めて Office アプリケーションが .NET Framework 3.5 を対象とするソリューションを読み込むときに、.NET Framework 3.5 用の Office 拡張機能がランタイムによって自動的にインストールされます。

 Office のインストール時に [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降が既に存在している場合でも、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降用の Office 拡張機能は Office と共にインストールされません。

 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 用の Office 拡張機能は、Office と共にインストールされます。 エンド ユーザーは、Windows Update をインストールすることで [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 用の Office 拡張機能を取得できます。

 ユーザーは、アプリケーションを使用するために必要な拡張機能であることを確認するには、するには、Visual Studio 2010 Tools for Office ランタイムが、ソリューションの前提条件として再頒布可能パッケージの最新バージョンを含めます。 前提条件の詳細については、次を参照してください。[展開 Office ソリューションの前提条件](https://msdn.microsoft.com/9f672809-43a3-40a1-9057-397ce3b5126e)します。

### <a name="install-the-runtime-by-using-the-runtime-redistributable"></a>再頒布可能パッケージのランタイムを使用して、ランタイムをインストールします。
 または、Office ソリューションを展開するときに、前提条件として再頒布可能パッケージを含めることによって、Visual Studio 2010 Tools for Office ランタイム再頒布可能パッケージを手動で実行してランタイムをインストールすることができます。

 Office ランタイム再頒布可能パッケージ、.NET Framework 3.5 用の Office 拡張機能および用の Office 拡張機能を Visual Studio 2010 Tools を使用して、ランタイムをインストールすると、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]以降がインストールされている場合、対応するバージョンの .NETFramework がコンピューターに存在します。 ランタイムをインストールするときにこれらのバージョンの .NET Framework の 1 つがコンピューターに存在しない場合、その時点では、存在しないバージョンの .NET Framework 用の Office 拡張機能はインストールされません。 存在しないバージョンの .NET Framework を後でインストールすると、次回、対応する Office 拡張機能を必要とするソリューションがインストールされたとき (ClickOnce を使用して配置されたソリューションと共にランタイムがインストールされた場合) または読み込まれたときに (Windows インストーラーを使用して配置されたソリューションと共にランタイムがインストールされた場合)、その拡張機能がランタイムによって自動的にインストールされます。

 ClickOnce ソリューションの必須コンポーネントを含む詳細については、次を参照してください。[方法。エンド ユーザー コンピューター上で Office ソリューションを実行するための前提条件のインストール方法](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98)を参照してください。 再頒布可能パッケージからランタイムを手動でインストールする方法の詳細については、次を参照してください。[方法。Visual Studio Tools for Office ランタイム再頒布可能パッケージをインストール](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)します。

## <a name="see-also"></a>関連項目
- [Visual Studio Tools for Office ランタイムの概要](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Visual Studio Tools for Office ランタイムのアセンブリ](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)
