---
title: ICorDebugNativeFrame2::IsChild 方法
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.IsChild Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::IsChild
helpviewer_keywords:
- IsChild method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsChild method [.NET Framework debugging]
ms.assetid: 9e2aae09-49cb-4fbd-81e5-e29cd864a88b
topic_type:
- apiref
ms.openlocfilehash: 0d65849aba08c7d143a6977e7dfb8cff85274a64
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695565"
---
# <a name="icordebugnativeframe2ischild-method"></a>ICorDebugNativeFrame2::IsChild 方法

判斷目前的框架是否為子框架。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
## <a name="parameters"></a>參數  

 `pIsChild`  
 擴展布林值，指定目前的框架是否為子框架。  
  
## <a name="return-value"></a>傳回值  

 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功傳回子狀態。|  
|E_FAIL|無法傳回子狀態。|  
|E_INVALIDARG|`pIsChild` 為 null。|  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>備註  

 `IsChild` `true` 如果您呼叫方法的框架物件是另一個框架的子系，則此方法會傳回。 如果是這種情況，請使用 [IsMatchingParentFrame](icordebugnativeframe2-ismatchingparentframe-method.md) 方法來檢查框架是否為其父代。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugNativeFrame2 介面](icordebugnativeframe2-interface.md)
- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
