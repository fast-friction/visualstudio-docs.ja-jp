---
title: プロパティは関連付けに関与しているため、削除できません
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e1890535fb008c8e8be6ee9dea0eda3ab3844da6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648141"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>プロパティ &lt;プロパティ名&gt; は関連付け &lt;関連付けの名前&gt; に関与しているため、削除できません

選択されたプロパティは、エラー メッセージに示されているクラス間の関連付けに対する**関連付けプロパティ**として設定されています。 プロパティがデータ クラス間の関連付けに関与している場合、そのプロパティを削除することはできません。

**関連付けプロパティ**をデータ クラスの別のプロパティに設定して、目的のプロパティが正常に削除されるようにします。

## <a name="to-correct-this-error"></a>このエラーを解決するには

1. **O/R デザイナー**で、エラー メッセージに示されているデータ クラスを接続する関連行を選択します。

2. 行をダブルクリックして、 **[関連付けエディター]** ダイアログ ボックスを開きます。

3. **[関連付けのプロパティ]** からプロパティを削除します。

4. プロパティの削除を再試行します。

## <a name="see-also"></a>関連項目

- [Visual Studio の LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)