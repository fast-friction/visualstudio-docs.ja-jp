﻿---
title: '方法: Visual Studio Tools for Office ランタイム再頒布可能パッケージをインストールする'
titleSuffix: ''
ms.custom: seodec18
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio]
- installing Office development tools in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 801486e7c0abfa2cb91f7fb7237cf3a48e8bc916
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985905"
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>方法: Visual Studio Tools for Office ランタイム再頒布可能パッケージをインストールする
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]の Microsoft Office 開発者ツールを使用して作成されたソリューションを実行する各コンピューターに、Visual Studio 2010 Tools for Office runtime をインストールする必要があります。 ランタイムは、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、および Microsoft Office をインストールすると自動的にインストールされます。 詳細については、「 [Visual Studio Tools for Office ランタイムのインストールシナリオ](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)」を参照してください。

[!include[Add-ins note](includes/addinsnote.md)]

 次の場合は、手動による以下のインストール手順を実行する必要があります。

- [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] をサーバーにインストールする必要がある場合。 たとえば、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> クラスを使用してサーバー上のドキュメント レベルのソリューションを管理する場合があります。

- Office ソリューションのその他の必須コンポーネントが既にインストールされているコンピューターにランタイムをインストールする必要がある場合。

    > [!NOTE]
    > .NET Framework および [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] をインストールするには、開発コンピューターの管理者である必要があります。

## <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>Visual Studio Tools for Office ランタイムをインストールするには

1. [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降をインストールします。

    - [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]をダウンロードするには、「 [Microsoft .NET Framework 4 (Web インストーラー)](https://www.microsoft.com/download/details.aspx?id=17851)」を参照してください。

    - [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]をダウンロードするには、「 [Microsoft .NET Framework 4 Client Profile (Web インストーラー)](https://www.microsoft.com/download/details.aspx?id=17113)」を参照してください。

    - [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]をダウンロードするには、「 [Microsoft .NET Framework 4.5](https://www.microsoft.com/download/details.aspx?id=30653)」を参照してください。

2. *Vstor_redist*を実行して [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]をインストールします。

     これらのセットアップファイルは、 [Visual Studio 2010 Tools For Office runtime](https://www.microsoft.com/download/details.aspx?id=56961)からダウンロードできます。 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] の必須コンポーネントは .NET Framework の場合と同じです。

     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] には、言語パックが用意されています。 Windows のインストールが英語以外の言語に設定されている場合、Windows と同じ言語でランタイム メッセージを表示できます。 同様に、エンド ユーザーが [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] をインストールし、英語以外の言語に設定されている Windows のインストールでソリューションを実行すると、Windows と同じ言語でランタイム メッセージが表示されます。 場合によっては、追加の言語パックが必要になる場合があります。 たとえば、Windows のコピーで複数の言語設定が使用されている場合、または既に [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]をインストールした後に別の言語に切り替える場合は、追加の言語パックが必要になることがあります。 言語パックは[、Microsoft Visual Studio 2010 Tools for the Microsoft Office system (version 4.0 runtime) language pack](https://www.microsoft.com/download/details.aspx?id=54246)で見つけることができます。

## <a name="see-also"></a>関連項目
- [Visual Studio &#40;での Office 開発の概要&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Office ソリューションを開発するようにコンピューターを構成する](../vsto/configuring-a-computer-to-develop-office-solutions.md)
- [方法: Office ソリューションを開発するようにコンピューターを構成する](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [方法: Office プライマリ相互運用機能アセンブリをインストールする](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [ServerDocument クラスを使用してサーバー上のドキュメントを管理する](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)
