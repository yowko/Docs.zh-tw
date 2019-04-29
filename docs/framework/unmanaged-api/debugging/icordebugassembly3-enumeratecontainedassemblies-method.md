---
title: ICorDebugAssembly3::EnumerateContainedAssemblies 方法
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54ccb52468a530280527252e0e0c43cc9edbb2c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645470"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a>ICorDebugAssembly3::EnumerateContainedAssemblies 方法
取得這個組件所包含之組件的列舉值。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppAssemblies`  
 [out]ICorDebugAssemblyEnum 介面物件，列舉值的位址指標。  
  
## <a name="return-value"></a>傳回值  
 如果這個 `S_OK` 物件是容器，則為 `ICorDebugAssembly3`；否則為 `S_FALSE` 且列舉是空的。  
  
## <a name="remarks"></a>備註  
 需要符號才能列舉所包含的組件。 如果不存在，則這個方法會傳回 `S_FALSE` 並且不會提供任何有效的列舉值。  
  
> [!NOTE]
>  這個方法僅適用於 .NET Native。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugAssembly3 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
