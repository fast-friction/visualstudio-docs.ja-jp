---
title: RegPkg Utility |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f811eb37da730d63e199a0e378b8a9122143649e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724444"
---
# <a name="regpkg-utility"></a>RegPkg ユーティリティ
> [!NOTE]
> Visual Studio でパッケージを登録するには、pkgdef ファイルを使用することをお勧めします。 これにより、システムレジストリにアクセスしなくても拡張機能をデプロイできます。これは、VSIX 配置に必要です。 Pkgdef ファイルは、 [Createpkgdef ユーティリティ](../../extensibility/internals/createpkgdef-utility.md)を使用して作成されます。 Visual Studio パッケージの配置の詳細については、「 [Visual Studio 拡張機能の配布](../../extensibility/shipping-visual-studio-extensions.md)」を参照してください。

 RegPkg ユーティリティは、VSPackage を [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] に登録し、デプロイ用に準備します。 このユーティリティは、VSPackage の開発中にバックグラウンドで使用されます。 実験用 hive で VSPackage をビルドして実行できるように、ビルドプロセスの一部として実行されます。

 RegPkg では、複数の形式でシステムレジストリスクリプトを生成できます。 これらのスクリプトは、.msi プロジェクトや Windows インストーラー XML ツールセットファイルなどの配置プロジェクトに組み込むことができます。

 通常、\VisualStudioIntegration\Tools\Bin\RegPkg.exe. は*Visual STUDIO SDK のインストールパス*> \< にあります。 RegPkg は、次の構文に従います。

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /root: ルートが指定された位置で登録を実行します

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ルート。

 /regfile: FileName は、レジストリを更新するのではなく、.reg ファイルを作成します。  /Vrgfile または/rgsfile または/wixfile. と共に使用することはできません。

 /rgsfile: FileName は、レジストリを更新するのではなく、.rgs ファイルを作成します。  /Vrgfile または/regfile または/wixfile. と共に使用することはできません。

 /vrgfile: FileName は、レジストリを更新するのではなく、vrg ファイルを作成します。  /Regfile または/rgsfile または/wixfile. と共に使用することはできません

 /rgm は、rgs ファイルに加えて、rgm ファイルを作成します。  /Rgsfile. と組み合わせる必要があります。

 /wixfile: FileName は、レジストリを更新するのではなく、Windows インストーラー XML ツールセットと互換性のあるファイルを作成します。  /Regfile または/rgsfile または/vrgfileと共に使用することはできません。

 /codebase は、アセンブリではなく、コードベースで登録を強制します。

 /アセンブリは、コードベースではなく、アセンブリに強制的に登録します。

 /unregister このパッケージの登録を解除します。  使用できません

 with/regfile または/vrgfile または/rgsfile または/wixfile.

## <a name="see-also"></a>関連項目
- [VSPackage](../../extensibility/internals/vspackages.md)
- [RegPkg パッケージ登録のトラブルシューティング](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)