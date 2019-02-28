---
title: ICorDebugProcess2 介面
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3009ee6a2ba22771a2132032744f76ca527c422
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965679"
---
# <a name="icordebugprocess2-interface"></a>ICorDebugProcess2 介面
ICorDebugProcess 介面，表示處理程序執行 managed 程式碼的邏輯擴充。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ClearUnmanagedBreakpoint 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)|移除指定之位移的先前呼叫所設定的中斷點`ICorDebugProcess2::SetUnmanagedBreakpoint`。|  
|[GetDesiredNGENCompilerFlags 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getdesiredngencompilerflags-method.md)|取得必須設為 common language runtime (CLR) 將影像載入處理序所參考的旗標`ICorDebugProcess2`。|  
|[GetReferenceValueFromGCHandle 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getreferencevaluefromgchandle-method.md)|取得指定已處理的記憶體回收的 managed 物件的參考指標。|  
|[GetThreadForTaskID 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getthreadfortaskid-method.md)|取得具有指定識別碼的工作正在執行的執行緒。|  
|[GetVersion 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getversion-method.md)|取得正在偵錯處理序正在執行的 CLR 版本。|  
|[SetDesiredNGENCompilerFlags 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)|設定所需的影像載入處理序偵錯在 just-in-time (JIT) 編譯器的旗標。|  
|[SetUnmanagedBreakpoint 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)|指定的原生映像的位移設定為未受管理的中斷點。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
