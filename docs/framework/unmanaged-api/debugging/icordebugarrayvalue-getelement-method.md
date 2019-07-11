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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 356f7ec9c50ce511883cbf0f5fbcb729493c92af
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737578"
---
# <a name="icordebugarrayvaluegetelement-method"></a>ICorDebugArrayValue::GetElement 方法
取得指定之陣列元素的值。  
  
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
 [in]這個維度的數目`ICorDebugArrayValue`物件。  
  
 此值也是的大小`indices`因為其大小的維度數目等於陣列`ICorDebugArrayValue`物件。  
  
 `indices`  
 [in]陣列的索引值，其中每個指定的維度內的位置`ICorDebugArrayValue`物件。  
  
 此值不能為 null。  
  
 `ppValue`  
 [out]ICorDebugValue 物件，表示指定的項目值的位址指標。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
