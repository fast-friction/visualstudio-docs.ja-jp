---
title: 'エラー: Web サーバーは要求されたリソース | を見つけることができませんでした。Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 1ceeaf30-918c-42bb-ace1-96944530fef3
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 555bb56ee84b7bc48f6b6453c11daef366f97e49
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2020
ms.locfileid: "75845117"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>エラー : Web サーバーでは要求されたリソースを見つけられませんでした
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

セキュリティ上の考慮から、IIS が汎用エラーを返しました。  
  
 考えられる原因の 1 つは、サーバーのセキュリティ構成です。 IIS 6.0 以前のバージョンでは、URLScan と呼ばれるアドオン プログラムを使用して、不適切で疑わしい要求を除外しました。 IIS 7.0 には、同じ目的の要求フィルターが組み込まれています。 いずれの場合も、要求フィルター処理の制限が厳しすぎると Visual Studio がサーバーをデバッグできないことがあります。  
  
 このエラーには、さまざまな原因が考えられます。 最も一般的な原因には、IIS のインストールまたは構成の問題、Web サイトの構成の問題、ファイル システムのアクセス許可の問題などがあります。 ブラウザーを使用してリソースへのアクセスを試すことができます。 IIS の構成方法によっては、サーバーでローカル ブラウザーを使用したり、IIS エラー ログを検査して詳細なエラー メッセージを確認したりする必要があります。  
  
 IIS のトラブルシューティングの詳細については、「[IIS Management and Administration (IIS の管理)](https://www.iis.net/learn/manage/provisioning-and-managing-iis/iis-management-and-administration)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [UrlScan セキュリティツール](/iis/extensions/working-with-urlscan/urlscan-3-reference)   
 [エラー: Web サーバーが制限され、デバッグの有効化に必要な DEBUG 動詞をブロックしています](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)
