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
ms.openlocfilehash: 213bee96531fa0bbc9bf0ae76b2505019833abfc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724698"
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
 在您想要評估其父狀態的框架物件指標。  
  
 `pIsParent`  
 [out] `true` 如果 `pPotentialParentFrame` 是目前框架的父系，則為，否則為 `false` 。  
  
## <a name="return-value"></a>傳回值  

 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功傳回父狀態。|  
|E_FAIL|無法傳回父狀態。|  
|E_INVALIDARG|`pPotentialParentFrame` 或 `pIsParent` 為 null。|  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>備註  

 `IsMatchingParentFrame``true`如果您傳遞給方法的框架物件是呼叫方法之框架物件的父系，則會傳回。 如果您在不是指定框架子系的框架上呼叫方法，則會傳回錯誤。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugNativeFrame2 介面](icordebugnativeframe2-interface.md)
- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
