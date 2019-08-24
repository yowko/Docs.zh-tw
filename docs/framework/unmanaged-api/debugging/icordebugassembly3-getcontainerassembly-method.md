---
title: ICorDebugAssembly3::GetContainerAssembly 方法
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4cda67145a0e624f87e93cf02ebdb6bc77c34d2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69987603"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a>ICorDebugAssembly3::GetContainerAssembly 方法
傳回這個 `ICorDebugAssembly3` 物件的容器組件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppAssembly`  
 代表容器元件之 ICorDebugAssembly 物件位址的指標, 如果方法呼叫失敗, 則為**null** 。  
  
## <a name="return-value"></a>傳回值  
 `S_OK`如果方法呼叫成功, 則為,否則, `S_FALSE`、和`ppAssembly`為**null**。  
  
## <a name="remarks"></a>備註  
 如果這個組件與其他組件已合併到單一容器組件內，這個方法會傳回該容器組件。 如需詳細資訊和術語, 請參閱[ICorDebugProcess6:: EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md)主題。  
  
> [!NOTE]
> 這個方法僅適用於 .NET Native。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugAssembly3 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
