---
title: Idiasymbol::get_virtualbasepointeroffset |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualBasePointerOffset method
ms.assetid: a4f2649c-6702-491c-90a1-d6d669258c51
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 57b6c71d5f4f5ced606d0c26cdbdbc8251c8d319
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2019
ms.locfileid: "64807866"
---
# <a name="idiasymbolgetvirtualbasepointeroffset"></a>IDiaSymbol::get_virtualBasePointerOffset
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

仮想基底ポインターのオフセットを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT get_virtualBasePointerOffset (   
   LONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]仮想基底ポインターのオフセットを返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
> 戻り値`S_FALSE`プロパティがシンボルを使用できないことを意味します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
