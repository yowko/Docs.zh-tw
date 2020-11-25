---
title: ICorDebugReferenceValue::SetValue 方法
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.SetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::SetValue
helpviewer_keywords:
- SetValue method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::SetValue method [.NET Framework debugging]
ms.assetid: 3d3f6eec-d772-401f-a028-1a2ecdc31e95
topic_type:
- apiref
ms.openlocfilehash: 3fdd3180a01e4609ac40fd358879c0d2569234ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728377"
---
# <a name="icordebugreferencevaluesetvalue-method"></a>ICorDebugReferenceValue::SetValue 方法

設定指定的記憶體位址。 也就是說，這個方法會將此 ICorDebugReferenceValue 設定為指向物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetValue (  
    [in] CORDB_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a>參數  

 `value`  
 在 `CORDB_ADDRESS` 值，指定此指向的物件位址 `ICorDebugReferenceValue` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
