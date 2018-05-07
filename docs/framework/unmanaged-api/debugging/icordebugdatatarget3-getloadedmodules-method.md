---
title: ICorDebugDataTarget3::GetLoadedModules 方法
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c51ce8ff76e0fc1588cdd136de83b77dcab0f10
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a>ICorDebugDataTarget3::GetLoadedModules 方法
取得到目前為止已載入的模組清單。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cRequestedModules`  
 [in] 要求該模組資訊的模組數目。  
  
 `pcFetchedModules`  
 [out] 傳回該模組資訊之模組數目的指標。  
  
 `pLoadedModules`  
 [out]陣列的指標[ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)提供下列資訊的物件載入的模組。  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  本方法只適用於 .NET 原生。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebugDataTarget3 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
