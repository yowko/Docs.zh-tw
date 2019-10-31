---
title: ICorDebugNativeFrame2::IsMatchingParentFrame 方法
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.IsMatchingParentFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::IsMatchingParentFrame
helpviewer_keywords:
- IsMatchingParentFrame method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsMatchingParentFrame method [.NET Framework debugging]
ms.assetid: d2ca20db-df22-4528-a0dd-a09ea62c8998
topic_type:
- apiref
ms.openlocfilehash: aa06b7db6b7371e66853ed242f5e118fb5e5ff0c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096193"
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a>ICorDebugNativeFrame2::IsMatchingParentFrame 方法
判斷指定的框架是否為目前框架的父系。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
## <a name="parameters"></a>參數  
 `pPotentialParentFrame`  
 在您想要針對父狀態評估之框架物件的指標。  
  
 `pIsParent`  
 [out] `true` 如果 `pPotentialParentFrame` 是目前框架的父系，則為，否則，`false`。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|父狀態已成功傳回。|  
|E_FAIL|無法傳回父系狀態。|  
|E_INVALIDARG|`pPotentialParentFrame` 或 `pIsParent` 為 null。|  
  
## <a name="exceptions"></a>例外狀況  
  
## <a name="remarks"></a>備註  
 如果您傳遞至方法的框架物件是呼叫方法之框架物件的父系，`IsMatchingParentFrame` 會傳回 `true`。 如果您在不是指定框架之子系的框架上呼叫方法，則會傳回錯誤。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugNativeFrame2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
