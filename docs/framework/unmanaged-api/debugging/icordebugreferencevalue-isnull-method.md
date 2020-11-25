---
title: ICorDebugReferenceValue::IsNull 方法
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.IsNull
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::IsNull
helpviewer_keywords:
- IsNull method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::IsNull method [.NET Framework debugging]
ms.assetid: 99e8c8d7-a1c0-47c8-9dbd-03e0b2bcb4d5
topic_type:
- apiref
ms.openlocfilehash: bcd4c8ba4b81821ae7dd9deaf0f76a76d335aff8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728390"
---
# <a name="icordebugreferencevalueisnull-method"></a>ICorDebugReferenceValue::IsNull 方法

取得值，這個值表示此 ICorDebugReferenceValue 是否為 null 值，在此情況下，不 `ICorDebugReferenceValue` 會指向物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsNull (  
    [out] BOOL   *pbNull  
);  
```  
  
## <a name="parameters"></a>參數  

 `pbNull`  
 擴展布林值的指標， `true` 如果這個 `ICorDebugReferenceValue` 物件為 null，則為，否則 `pbNull` 為 `false` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
