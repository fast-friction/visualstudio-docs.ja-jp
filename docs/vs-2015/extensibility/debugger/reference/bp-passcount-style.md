---
title: BP_PASSCOUNT_STYLE |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: deb4ce7c464e8518faff55957e1873ef1cd92c39
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "68153367"
---
# <a name="bppasscountstyle"></a>BP_PASSCOUNT_STYLE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

ブレークポイントを発生させる原因となるブレークポイント パスの数に関連付けられている条件を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
typedef DWORD BP_PASSCOUNT_STYLE;  
```  
  
```csharp  
public enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
```  
  
## <a name="members"></a>メンバー  
 BP_PASSCOUNT_NONE  
 ブレークポイントのパスの数のスタイルを指定しません。  
  
 BP_PASSCOUNT_EQUAL  
 等しいブレークポイント パス数のスタイルを設定します。 ブレークポイントは、ブレークポイントにヒットした回数がパスの数と等しい場合に発生します。  
  
 BP_PASSCOUNT_EQUAL_OR_GREATER  
 ブレークポイント パスの数のスタイルを以上に設定します。 ブレークポイントは、ブレークポイントのヒット カウント数がパスの数以上である場合に発生します。  
  
 BP_PASSCOUNT_MOD  
 指定します、剰余数を渡します。 たとえば、パスの数が、型の場合`BP_PASSCOUNT_MOD`パスの数の値が 4、ヒット カウントが 4 の倍数たびに、ブレークポイントが起動します。  
  
## <a name="remarks"></a>Remarks  
 使用、`stylePassCount`のメンバー、 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)構造体のメンバーではさらに、 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)と[BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)構造体。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
