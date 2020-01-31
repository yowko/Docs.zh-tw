---
title: ICorDebugAssembly3::EnumerateContainedAssemblies 方法
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
ms.openlocfilehash: 616675f839e562227558ece440bdfdf497747572
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784565"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a>ICorDebugAssembly3::EnumerateContainedAssemblies 方法
取得這個組件所包含之組件的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppAssemblies`  
 [out] 代表列舉值之 ICorDebugAssemblyEnum 介面物件的位址指標。  
  
## <a name="return-value"></a>傳回值  
 如果這個 `S_OK` 物件是容器，則為 `ICorDebugAssembly3`；否則為 `S_FALSE` 且列舉是空的。  
  
## <a name="remarks"></a>備註  
 需要符號才能列舉所包含的組件。 如果不存在，則這個方法會傳回 `S_FALSE` 並且不會提供任何有效的列舉值。  
  
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
