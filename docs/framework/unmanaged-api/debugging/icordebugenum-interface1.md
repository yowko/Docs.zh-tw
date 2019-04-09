---
title: ICorDebugEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum
helpviewer_keywords:
- ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 80be7efe-2c32-4b9f-8c52-40c6f6268219
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9afaeebfdb98a404ea53b0b5ec147f8c8104e14d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148807"
---
# <a name="icordebugenum-interface"></a>ICorDebugEnum 介面

做為 偵錯的應用程式所使用的列舉值的抽象基底介面。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Clone 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-clone-method.md)|建立一份這`ICorDebugEnum`物件。|  
|[GetCount 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-getcount-method.md)|列舉中取得的項目數。|  
|[Reset 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-reset-method.md)|將游標移至列舉型別的開頭。|  
|[Skip 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-skip-method.md)|將游標移往前列舉中所指定的項目數。|  
  
## <a name="remarks"></a>備註  
 下列的列舉值衍生自`ICorDebugEnum`:  
  
-   "ICorDebugAppDomainEnum"  
  
-   「 ICorDebugAssemblyEnum"  
  
-   [ICorDebugBlockingObjectEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
  
-   "ICorDebugBreakpointEnum"  
  
-   「 ICorDebugChainEnum"  
  
-   「 ICorDebugCodeEnum"  
  
-   「 ICorDebugErrorInfoEnum"  
  
-   [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
  
-   "ICorDebugFrameEnum"  
  
-   [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
  
-   [ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
  
-   [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
  
-   [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
  
-   「 ICorDebugModuleEnum"  
  
-   "ICorDebugObjectEnum"  
  
-   "ICorDebugProcessEnum"  
  
-   "ICorDebugStepperEnum"  
  
-   「 ICorDebugThreadEnum"  
  
-   「 ICorDebugTypeEnum"  
  
-   「 ICorDebugValueEnum"  
  
-   [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
