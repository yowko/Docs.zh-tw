---
title: ICorDebugBlockingObjectEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugBlockingObjectEnum.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBlockingObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
- ICorDebugBlockingObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 0121753f-ebea-48d0-aeb2-ed7fda76dc60
topic_type:
- apiref
ms.openlocfilehash: 232068a5fee8f7bd3dfbddf4d9452e80d6fd6170
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719186"
---
# <a name="icordebugblockingobjectenumnext-method"></a>ICorDebugBlockingObjectEnum::Next 方法

從目前位置開始，取得列舉中指定的 [CorDebugBlockingObject](cordebugblockingobject-structure.md) 物件數目。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Next([in] ULONG  celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                           CorDebugBlockingObject values[],  
             [out] ULONG *pceltFetched;  
```  
  
## <a name="parameters"></a>參數  

 `celt`  
 在要取出的物件數目。  
  
 `values`  
 擴展 [CorDebugBlockingObject](cordebugblockingobject-structure.md) 物件之指標的陣列。  
  
 `pceltFetched`  
 擴展已抓取之物件數目的指標。  
  
## <a name="return-value"></a>傳回值  

 這個方法會傳回下列特定的 HRESULT。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|S_FALSE|`pceltFetched` 不等於 `celt`。|  
  
## <a name="remarks"></a>備註  

 這個方法的功能與一般 COM 列舉值相同。  
  
 輸入陣列值必須至少為大小 `celt` 。 陣列將會填入列舉中的下一個 `celt` 值，或如果保留的值小於，則會填入所有剩餘的值 `celt` 。 當此方法傳回時， `pceltFetched` 會填入已取出的值數目。 如果 `values` 包含不正確指標或指向小於的緩衝區， `celt` 或如果 `pceltFetched` 是不正確指標，則結果為未定義。  
  
> [!NOTE]
> 雖然不需要釋出 [CorDebugBlockingObject](cordebugblockingobject-structure.md) 結構，但它裡面的 "ICorDebugValue" 介面的確需要釋出。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugDataTarget 介面](icordebugdatatarget-interface.md)
- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
