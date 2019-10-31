---
title: ICorDebugProcess2 Interface
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2
helpviewer_keywords:
- ICorDebugProcess2 interface [.NET Framework debugging]
ms.assetid: 73332138-5fea-441f-b893-61af87d45a42
topic_type:
- apiref
ms.openlocfilehash: 213eb86c36225a6194af83c04c469fbe0cc51b63
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137158"
---
# <a name="icordebugprocess2-interface"></a>ICorDebugProcess2 Interface
ICorDebugProcess 介面的邏輯延伸，代表執行 managed 程式碼的進程。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ClearUnmanagedBreakpoint 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)|移除先前呼叫 `ICorDebugProcess2::SetUnmanagedBreakpoint`所設定之指定位移處的中斷點。|  
|[GetDesiredNGENCompilerFlags 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getdesiredngencompilerflags-method.md)|取得必須針對 common language runtime （CLR）設定的旗標，以將影像載入此 `ICorDebugProcess2`所參考的進程中。|  
|[GetReferenceValueFromGCHandle 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getreferencevaluefromgchandle-method.md)|取得具有垃圾收集控制碼之指定 managed 物件的參考指標。|  
|[GetThreadForTaskID 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getthreadfortaskid-method.md)|取得具有指定識別碼之工作執行所在的執行緒。|  
|[GetVersion 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getversion-method.md)|取得正在進行偵錯工具的 CLR 版本。|  
|[SetDesiredNGENCompilerFlags 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)|設定即時（JIT）編譯器所需的旗標，以將影像載入正在進行調試的進程。|  
|[SetUnmanagedBreakpoint 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)|在指定的原生映射位移處設定非受控中斷點。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
