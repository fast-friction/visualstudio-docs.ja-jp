---
title: 要素 (Visual Studio テンプレート) を参照 |Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Reference
helpviewer_keywords:
- Reference element [Visual Studio templates]
- <Reference> element [Visual Studio templates]
ms.assetid: 852772ea-c324-42e9-8c8a-6d565414a109
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 46c9cbde1186a0dd764c3075ef1566eb1fd5ea07
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334386"
---
# <a name="reference-element-visual-studio-templates"></a>Reference 要素 (Visual Studio テンプレート)
項目がプロジェクトに追加されたときに追加するアセンブリ参照を指定します。

 \<VSTemplate> \<TemplateContent> \<References> \<Reference>

## <a name="syntax"></a>構文

```xml
<Reference>
    <Assembly> ... </Assembly>
</Reference>
```

## <a name="attributes-and-elements"></a>属性と要素
 以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性
 なし。

### <a name="child-elements"></a>子要素

|要素|説明|
|-------------|-----------------|
|[Assembly](../extensibility/assembly-element-visual-studio-templates.md)|必須の要素です。<br /><br /> そのアセンブリの参照をプロジェクトに追加するテンプレートを使用して、アセンブリに関する情報を指定します。 1 つあります`Assembly`内の要素すべて`Reference`要素。|

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|[参照](../extensibility/references-element-visual-studio-templates.md)|このテンプレートはプロジェクトに追加するアセンブリ参照をグループ化します。|

## <a name="remarks"></a>Remarks
 `Reference` は `References` に必須の子要素です。

 `Reference`と`References`要素でのみ使用できます *.vstemplate*を持つファイルを`Type`属性の値`Item`します。

## <a name="example"></a>例
 次の例を示しています、`TemplateContent`項目テンプレートの要素。 この XML への参照の追加、 *System.dll*と*System.Data.dll*アセンブリ。

```xml
<TemplateContent>
    <References>
        <Reference>
            <Assembly>
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
            </Assembly>
        </Reference>
        <Reference>
            <Assembly>
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
            </Assembly>
        </Reference>
    </References>
    ...
</TemplateContent>
```

## <a name="see-also"></a>関連項目
- [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)
- [プロジェクト テンプレートと項目テンプレートを作成する](../ide/creating-project-and-item-templates.md)
