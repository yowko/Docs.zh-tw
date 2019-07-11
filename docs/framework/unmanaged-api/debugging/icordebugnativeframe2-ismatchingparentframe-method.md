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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e215cf4f6d6c3cfde3fa723ecae67aa77e189917
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757066"
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a>ICorDebugNativeFrame2::IsMatchingParentFrame 方法
判斷指定的範圍是否為目前的畫面格的父代。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
## <a name="parameters"></a>參數  
 `pPotentialParentFrame`  
 [in]您想要評估父狀態框架物件的指標。  
  
 `pIsParent`  
 [out]`true`如果`pPotentialParentFrame`是目前畫面格的父代，則為`false`。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功地傳回父代的狀態。|  
|E_FAIL|不會傳回父代的狀態。|  
|E_INVALIDARG|`pPotentialParentFrame` 或 `pIsParent` 為 null。|  
  
## <a name="exceptions"></a>例外狀況  
  
## <a name="remarks"></a>備註  
 `IsMatchingParentFrame` 傳回`true`您傳遞給方法的框架物件是否在其呼叫此方法的畫面格物件的父系。 如果您不是為指定框架的子系框架上呼叫方法，它會傳回錯誤。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugNativeFrame2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
