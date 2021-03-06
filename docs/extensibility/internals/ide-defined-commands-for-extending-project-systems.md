---
title: プロジェクトシステムを拡張するための IDE 定義コマンド |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1c8be1cff099a713413957cfa5f8b3f383ca4bae
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186331"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>プロジェクト システムを拡張するための IDE 定義コマンド
プロジェクトシステムを拡張する場合は、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE によって提供されるコマンドとコマンドグループを使用できます。

 以下のセクションでは、プロジェクトシステムの拡張に特に役立つコマンド項目の一覧を示します。

## <a name="command-menus"></a>コマンドメニュー
 次の表は、プロジェクトエクステンダーを呼び出す高レベルのコマンドを配置するのに役立つコマンドメニューを示しています。

|コマンドメニュー|説明|
|------------------|-----------------|
|IDM_VS_MENU_PROJECT|**プロジェクト**のトップレベルメニュー。|
|IDM_VS_TOOL_PROJWIN|**ソリューションエクスプローラー**ツールバー。|

## <a name="shortcut-menus"></a>ショートカット メニュー
 次の表は、**ソリューションエクスプローラー**で1つのノードが選択されたとき、または選択されたすべてのノードが同じ種類である場合に、**ソリューションエクスプローラー**に複数の同種選択があるときに適用されるショートカットメニューを示しています。

|ショートカットメニュー|説明|
|-------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|プロジェクトノードが選択されたときに適用されます。|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|ファイルが選択されたときに適用されます。|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|フォルダーが選択されたときに適用されます。|
|IDM_VS_CTXT_WEBREFFOLDER|Web 参照フォルダーが選択されたときに適用されます。|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|"参照" と呼ばれる [参照] ルートノードが選択されている場合に適用されます。|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|参照ノードが選択されたときに適用されます。これには、アセンブリ、COM、およびプロジェクト参照のみが含まれます。 には、Web 参照は含まれません。|

 次の表は、**ソリューションエクスプローラー**の選択範囲が複数の階層にまたがっている場合に適用されるショートカットメニューを示しています。

|ショートカットメニュー|説明|
|-------------------|-----------------|
|IDM_VS_CTXT_XPROJ_SLNPROJ|現在の選択範囲にソリューションノードとルートプロジェクトノードが含まれている場合に適用されます。|
|IDM_VS_CTXT_XPROJ_SLNITEM|現在の選択範囲にソリューションノードとプロジェクト項目が含まれている場合に適用されます。|
|IDM_VS_CTXT_XPROJ_MULTIPROJ|現在の選択範囲が複数のルートプロジェクトノードで構成されている場合に適用されます。|
|IDM_VS_CTXT_XPROJ_PROJITEM|現在の選択範囲にルートプロジェクトノードとプロジェクト項目が混在している場合に適用されます。 また、選択内容にソリューションノードが含まれる場合もあります。|
|IDM_VS_CTXT_XPROJ_MULTIITEM|現在の選択項目にソリューション内の複数のプロジェクトのプロジェクト項目が含まれている場合、または同じプロジェクトで異なる種類の項目が選択されている場合に適用されます。|

## <a name="command-groups"></a>コマンドグループ
 次の表に、プロジェクトを拡張するときに使用できるコマンドグループと、<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> ショートカットメニューを使用してアクセスできるコマンドグループを示します。

|コマンドグループ|説明|
|-------------------|-----------------|
|IDG_VS_CTXT_PROJECT_BUILD|プロジェクトをビルド、リビルド、および配置するためのコマンドです。|
|IDG_VS_CTXT_COMPILELINK|プロジェクトをコンパイルおよびリンクするためのコマンドです。|
|IDG_VS_CTXT_PROJECT_CONFIG|プロジェクト構成とビルド順序を設定するコマンド。|
|IDG_VS_CTXT_PROJECT_ADD|プロジェクトに項目を追加するコマンド。|
|IDG_VS_CTXT_PROJECT_START|F5 キーに関連付けられているスタートアッププロジェクトを設定するコマンド。|
|IDG_VS_CTXT_PROJECT_SAVE|プロジェクト項目を保存するためのコマンドです。|
|IDG_VS_CTXT_PROJECT_DEBUG|デバッグ用コマンド。|
|IDG_VS_CTXT_PROJECT_SCC|ソース管理のコマンド。|
|IDG_VS_CTXT_PROJECT_TRANSFER|切り取り、コピー、および貼り付け操作用のコマンド。|
|IDG_VS_CTXT_PROJECT_PROPERTIES|**[プロジェクトのプロパティ]** ダイアログボックスへのアクセスを提供するコマンド。|

## <a name="see-also"></a>関連項目

- [VSPackage でユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [再利用可能なボタンのグループの作成](../../extensibility/creating-reusable-groups-of-buttons.md)