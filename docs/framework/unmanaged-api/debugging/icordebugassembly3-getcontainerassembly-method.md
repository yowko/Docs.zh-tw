---
title: ICorDebugAssembly3::GetContainerAssembly 方法
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
ms.openlocfilehash: 969cca6d5613670fc4b26fc973785b4874c3684c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778064"
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
 代表容器元件之 ICorDebugAssembly 物件位址的指標，如果方法呼叫失敗，則為**null** 。  
  
## <a name="return-value"></a>傳回值  
 如果方法呼叫成功，則 `S_OK`;否則，`S_FALSE`，且 `ppAssembly` 為**null**。  
  
## <a name="remarks"></a>備註  
 如果這個組件與其他組件已合併到單一容器組件內，這個方法會傳回該容器組件。 如需詳細資訊和術語，請參閱[ICorDebugProcess6：： EnableVirtualModuleSplitting](icordebugprocess6-enablevirtualmodulesplitting-method.md)主題。  
  
> [!NOTE]
> 這個方法僅適用於 .NET Native。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugAssembly3 介面](icordebugassembly3-interface.md)
- [偵錯介面](debugging-interfaces.md)
