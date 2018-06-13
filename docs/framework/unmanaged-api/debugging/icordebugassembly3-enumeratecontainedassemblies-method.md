---
title: ICorDebugAssembly3::EnumerateContainedAssemblies 方法
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb84efe78568bbae03f76efc456fc8ae605e4db9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404832"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a>ICorDebugAssembly3::EnumerateContainedAssemblies 方法
取得這個組件所包含之組件的列舉值。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppAssemblies`  
 [out]ICorDebugAssemblyEnum 介面物件的列舉值的位址指標。  
  
## <a name="return-value"></a>傳回值  
 如果這個 `S_OK` 物件是容器，則為 `ICorDebugAssembly3`；否則為 `S_FALSE` 且列舉是空的。  
  
## <a name="remarks"></a>備註  
 需要符號才能列舉所包含的組件。 如果不存在，則這個方法會傳回 `S_FALSE` 並且不會提供任何有效的列舉值。  
  
> [!NOTE]
>  本方法只適用於 .NET 原生。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebugAssembly3 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
