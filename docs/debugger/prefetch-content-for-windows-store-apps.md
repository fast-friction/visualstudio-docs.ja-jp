---
title: UWP アプリでプリフェッチされるコンテンツを使用してデバッグする |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 28a73974a71df7fa652e4b246043e901df76e94c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2019
ms.locfileid: "72730573"
---
# <a name="debug-uwp-apps-using-prefetched-content-in-visual-studio"></a>Visual Studio でプリフェッチされるコンテンツを使用して UWP アプリをデバッグする

 UWP アプリの応答性を高めるために、web ページやイメージなどの一部の web コンテンツをアプリの[WinINet](/windows/desktop/WinInet/about-wininet)キャッシュにプリロードするように Windows に要求できます。 この機能をプリフェッチと呼びます。 これは起動時に使用されるコンテンツに特に効果的ですが、他の頻繁に使用するコンテンツをプリフェッチすることもできます。 [Windows.Networking.BackgroundTransfer.ContentPrefetcher](/uwp/api/Windows.Networking.BackgroundTransfer.ContentPrefetcher) クラスのメソッドを使用すると、プリロードするコンテンツの URI を指定できます。 アプリに ContentPrefetcher 機能を追加する方法の例については、Windows SDK の「[Content prefetch sample](https://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309)」 (コンテンツのプリフェッチの例) を参照してください。

 Windows は、プリフェッチを行う必要がある場合およびダウンロードするリソースを決定するためにヒューリスティックを使用します。 このヒューリスティックでは、システム ネットワークおよび電力条件、ユーザー アプリの使用履歴、および以前のプリフェッチの結果を考慮します。 Visual Studio では、**Trigger Windows Store App Prefetch** コマンドを使用することで、Windows に ContentPrefetcher ヒューリスティックを無視させ、さらに指定されたすべての Web コンテンツをプリロードさせることができます。 これは、既知の状態 (読み込まれている、または読み込まれていない) でプリフェッチするコンテンツでアプリの動作またはパフォーマンスをテストする場合に役立ちます。

## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>ContentPrefetcher で指定されるリソースのプリロードを強制するには
 この手順では、ContentPrefetcher 機能が既に設定されていて、アプリ プロジェクトでプリロードするコンテンツ URI が指定されていると仮定しています。 指定されたリソースが新しいまたは変更されている場合にコンテンツのプリロードを強制するには、**Trigger Windows Store App Prefetch** コマンドを選択する前にアプリを開始および停止する必要があります。 まず、アプリを実行して、URI を登録します。 **Trigger Windows Store App Prefetch** コマンドによって、ContentPrefetcher がコンテンツをダウンロードし、キャッシュに追加するように強制されます。 アプリの後続の実行で、コンテンツがプリロードされたと見なすことができます。

1. アプリを開始して、アプリでプリフェッチ コンテンツ URI を登録します。 **[デバッグ]** メニューで、 **[デバッグの開始]** を選択します (キーボード ショートカット: F5 キー)。

2. **[デバッグ]** メニューで、 **[デバッグの停止]** を選択します (キーボード ショートカット: Shift + F5 キー)。

3. **[デバッグ]** メニューで、 **[その他のデバッグ ターゲット]** をクリックし、 **[Windows ストア アプリ プリフェッチのトリガー]** をクリックします。

   プリフェチした Web リソースでアプリをデバッグ、テスト、または分析できるようになりました。

> [!NOTE]
> 指定された Web コンテンツを追加または変更するたびにこの手順を繰り返します。

## <a name="see-also"></a>関連項目
- [ブログの投稿: Visual Studio 2013 Update 2 で Windows ストアアプリのプリフェッチをトリガーする](https://devblogs.microsoft.com/devops/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2/)