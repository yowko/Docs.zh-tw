---
title: ICorDebugFunction3 介面
ms.date: 03/30/2017
api_name:
- ICorDebugFunction3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b22717b9-ead5-4eea-887e-789b52d613dc
topic_type:
- apiref
ms.openlocfilehash: 7ef983c2f0785cb97baf8ba1ad3483b46c08af9a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788663"
---
# <a name="icordebugfunction3-interface"></a>ICorDebugFunction3 介面
[.NET Framework 4.5.2 與更新版本提供支援]  
  
 以邏輯方式延伸 ICorDebugFunction 介面，以提供對 ReJIT 要求之程式碼的存取。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetActiveReJitRequestILCode 方法](icordebugfunction3-getactiverejitrequestilcode-method.md)|取得[ICorDebugILCode](icordebugilcode-interface.md)的介面指標，其中包含來自作用中 ReJIT 要求的 IL。|  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
- [ReJIT：使用說明指南](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
