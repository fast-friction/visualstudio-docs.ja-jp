---
title: 'CA2224: オーバーロードする operator equals | で equals をオーバーライドします。Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d35052bb2a1efb1a466ffc67c95c83e5b3a76533
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671880"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224: オーバーロードする演算子 equals で Equals をオーバーライドします
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|カテゴリ|Microsoft. 使用方法|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 パブリック型は等値演算子を実装しますが、<xref:System.Object.Equals%2A?displayProperty=fullName> をオーバーライドしません。

## <a name="rule-description"></a>規則の説明
 等値演算子は、<xref:System.Object.Equals%2A> メソッドの機能にアクセスするための構文的に便利な方法として使用することを意図しています。 等値演算子を実装する場合、そのロジックは <xref:System.Object.Equals%2A> のロジックと同じである必要があります。

 コードC#がこの規則に違反している場合、コンパイラは警告を発行します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、等値演算子の実装を削除するか、<xref:System.Object.Equals%2A> をオーバーライドして、2つのメソッドが同じ値を返すようにする必要があります。 等値演算子によって不整合な動作が発生しない場合は、基底クラスの <xref:System.Object.Equals%2A> メソッドを呼び出す <xref:System.Object.Equals%2A> の実装を指定することで、違反を修正できます。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 等値演算子が <xref:System.Object.Equals%2A> の継承された実装と同じ値を返す場合、この規則からの警告を抑制するのは安全です。 例のセクションには、この規則からの警告を安全に抑制できる型が含まれています。

## <a name="examples-of-inconsistent-equality-definitions"></a>一貫性のない等値定義の例

### <a name="description"></a>説明
 次の例は、一貫性のない定義を持つ型の等価性を示しています。 `BadPoint` は、等値演算子のカスタム実装を提供することで等値の意味を変更しますが、同じように動作するように <xref:System.Object.Equals%2A> をオーバーライドしません。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorEqualsRequiresEquals/cs/FxCop.Usage.OperatorEqualsRequiresEquals.cs#1)]

## <a name="example"></a>例
 次のコードでは `BadPoint` の動作をテストします。

 [!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestOperatorEqualsRequiresEquals/cs/FxCop.Usage.TestOperatorEqualsRequiresEquals.cs#1)]

 この例を実行すると、次の出力が生成されます。

 **a = ([0] 1, 1) と b = ([1] 2, 2) は等しいか?** **A = = b 
 ませんか?@No__t_3** **a1 と a は同じですか?はい**
**a1 = = a?はい**
**b と bcopy は同じですか?@No__t_9** **b = = bcopy?はい**
## <a name="example"></a>例
 次の例は、技術的にはこの規則に違反するが、一貫性のない方法で動作しない型を示しています。

 [!code-csharp[FxCop.Usage.ValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ValueTypeEquals/cs/FxCop.Usage.ValueTypeEquals.cs#1)]

## <a name="example"></a>例
 次のコードでは `GoodPoint` の動作をテストします。

 [!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestValueTypeEquals/cs/FxCop.Usage.TestValueTypeEquals.cs#1)]

 この例を実行すると、次の出力が生成されます。

 **a = (1, 1) と b = (2, 2) は等しいか?** **A = = b 
 ませんか?@No__t_3** **a1 と a は同じですか?はい**
**a1 = = a?はい**
**b と bcopy は同じですか?はい**
**b = = bcopy?はい**
## <a name="class-example"></a>クラスの例

### <a name="description"></a>説明
 次の例は、この規則に違反するクラス (参照型) を示しています。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassViolation/cs/FxCop.Usage.OverrideEqualsClassViolation.cs#1)]

## <a name="example"></a>例
 次の例では、<xref:System.Object.Equals%2A?displayProperty=fullName> をオーバーライドすることによって違反を修正します。

 [!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassFixed/cs/FxCop.Usage.OverrideEqualsClassFixed.cs#1)]

## <a name="structure-example"></a>構造体の例

### <a name="description"></a>説明
 次の例は、この規則に違反する構造体 (値型) を示しています。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructViolation/cs/FxCop.Usage.OverrideEqualsStructViolation.cs#1)]

## <a name="example"></a>例
 次の例では、<xref:System.ValueType.Equals%2A?displayProperty=fullName> をオーバーライドすることによって違反を修正します。

 [!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructFixed/cs/FxCop.Usage.OverrideEqualsStructFixed.cs#1)]

## <a name="related-rules"></a>関連規則
 [CA1046: 参照型で、演算子 equals をオーバーロードしないでください](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: 演算子オーバーロードには名前付けされた代替が存在します](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: 演算子は対称型オーバーロードを含まなければなりません](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2218: オーバーライドする Equals で GetHashCode をオーバーライドします](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: ValueType.Equals のオーバーライドで、演算子 equals をオーバーロードします](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
