---
title: PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS 列挙型 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1a41b642-c9a9-4d83-b943-d59b232eebf6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 322f6f3352c1b0dfad4572d55e1ebe2388c8cc4a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62823635"
---
# <a name="profilerheapobjectrelationshipflags-enumeration"></a>PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS 列挙型
オブジェクト リレーションシップ内でこのヒープ オブジェクトが指しているものが、Getter または Setter メソッドであることを表すフラグです。 使用される、 [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md)メソッドで PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS の値が指定した場合、`enumFlags`パラメーター。  
  
## <a name="syntax"></a>構文  
  
```cpp
typedef [v1_enum] enum {    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE                      = 0x00000000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR           = 0x00010000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR           = 0x00020000,} PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|[値]|説明|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE|0x00000000|オブジェクト リレーションシップ内でこのヒープ オブジェクトが指しているものは、Getter メソッド、Setter メソッドのいずれとしても認識されません。|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR|0x00010000|オブジェクト リレーションシップ内でヒープ オブジェクトは Getter メソッドを指しています。 この情報は、の上位 2 バイト (16 ビット) に格納されますが、 [PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md)フィールド。|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR|0x00020000|オブジェクト リレーションシップ内でヒープ オブジェクトは Setter メソッドを指しています。 この情報は、`PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo` フィールドの上位 2 バイト (16 ビット) に格納されます。|