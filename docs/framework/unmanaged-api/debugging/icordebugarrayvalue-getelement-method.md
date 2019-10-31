---
title: ICorDebugArrayValue::GetElement 方法
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElement
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElement
helpviewer_keywords:
- GetElement method [.NET Framework debugging]
- ICorDebugArrayValue::GetElement method [.NET Framework debugging]
ms.assetid: 7ac3cba5-c282-402e-b7ef-b46634f5176b
topic_type:
- apiref
ms.openlocfilehash: 3d45caae56403d77776f1a8adbb5fb9c368ff105
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088497"
---
# <a name="icordebugarrayvaluegetelement-method"></a>ICorDebugArrayValue::GetElement 方法
取得給定陣列元素的值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]   
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a>參數  
 `cdim`  
 在這個 `ICorDebugArrayValue` 物件的維度數目。  
  
 這個值也是 `indices` 陣列的大小，因為它的大小等於 `ICorDebugArrayValue` 物件的維度數目。  
  
 `indices`  
 在索引值的陣列，其中每一個都指定 `ICorDebugArrayValue` 物件之維度中的位置。  
  
 此值不得為 null。  
  
 `ppValue`  
 脫銷ICorDebugValue 物件位址的指標，表示指定元素的值。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
