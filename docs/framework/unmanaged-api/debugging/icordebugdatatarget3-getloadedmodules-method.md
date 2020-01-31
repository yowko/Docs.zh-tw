---
title: ICorDebugDataTarget3::GetLoadedModules 方法
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
ms.openlocfilehash: d4c22146422085daa4dc9d90ae5b3735a12500c2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793560"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a>ICorDebugDataTarget3::GetLoadedModules 方法
取得到目前為止已載入的模組清單。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
## <a name="parameters"></a>參數  
 `cRequestedModules`  
 [in] 要求該模組資訊的模組數目。  
  
 `pcFetchedModules`  
 [out] 傳回該模組資訊之模組數目的指標。  
  
 `pLoadedModules`  
 脫銷[ICorDebugLoadedModule](icordebugloadedmodule-interface.md)物件陣列的指標，提供已載入模組的相關資訊。  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個方法僅適用於 .NET Native。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugDataTarget3 介面](icordebugdatatarget3-interface.md)
- [偵錯介面](debugging-interfaces.md)
