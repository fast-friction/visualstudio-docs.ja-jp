---
title: EnableEditOfLocationField 要素 (Visual Studio テンプレート) |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- EnableEditOfLocationField (Visual Studio project templates)
ms.assetid: 51a91963-8a3f-4741-928e-bc90c11473bb
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6823b462f884e06e1729c9bb4777cc166b34ea7a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204619"
---
# <a name="enableeditoflocationfield-element-visual-studio-templates"></a>EnableEditOfLocationField 要素 (Visual Studio テンプレート)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ユーザーが [場所] フィールドを編集できるかどうかを指定します。  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<EnableEditOfLocationField >  
  
## <a name="syntax"></a>構文  
  
```  
<EnableEditOfLocationField> true/false </EnableEditOfLocationField>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必須の要素です。<br /><br /> テンプレートをカテゴリに分類し、 **[新しいプロジェクト]** ダイアログ ボックス、または **[新しい項目の追加]** ダイアログ ボックスでどのように表示させるかを定義します。|  
  
## <a name="text-value"></a>テキスト値  
 テキスト値が必要です。  
  
 テキストがいずれかにする必要があります`true`または`false`かを示す、ユーザーが編集できるかどうか、**場所**上のテキスト ボックス、**新しいプロジェクト** ダイアログ ボックス。  
  
## <a name="remarks"></a>Remarks  
 `EnableEditOfLocationField` は、省略可能な要素です。 既定値は`true`、ユーザーがの値を編集することができます、**場所**テキスト ボックスに、**新しいプロジェクト** ダイアログ ボックス。  
  
 **新しいプロジェクト** ダイアログ ボックスで、**場所**テキスト ボックスは、新しいプロジェクトが保存されているディレクトリを指定します。  
  
## <a name="example"></a>例  
 [!INCLUDE[csprcs](../includes/csprcs-md.md)] Windows アプリケーションでのメタデータの例を次に示します。  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <EnableEditOfLocationField>false</EnableEditOfLocationField>  
        <EnableLocationBrowseButton>false</EnableLocationBrowseButton>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)
