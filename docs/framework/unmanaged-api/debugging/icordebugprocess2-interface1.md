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
ms.openlocfilehash: f1a30c197373928ec10c2b84de4e805b94ea2384
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724503"
---
# <a name="icordebugprocess2-interface"></a>ICorDebugProcess2 Interface

ICorDebugProcess 介面的邏輯擴充，表示執行 managed 程式碼的進程。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ClearUnmanagedBreakpoint 方法](icordebugprocess2-clearunmanagedbreakpoint-method.md)|移除在先前的呼叫所設定之指定位移上的中斷點 `ICorDebugProcess2::SetUnmanagedBreakpoint` 。|  
|[GetDesiredNGENCompilerFlags 方法](icordebugprocess2-getdesiredngencompilerflags-method.md)|取得必須針對 common language runtime (CLR) 所設定的旗標，以將影像載入這個所參考的進程 `ICorDebugProcess2` 。|  
|[GetReferenceValueFromGCHandle 方法](icordebugprocess2-getreferencevaluefromgchandle-method.md)|取得具有垃圾收集控制碼之指定 managed 物件的參考指標。|  
|[GetThreadForTaskID 方法](icordebugprocess2-getthreadfortaskid-method.md)|取得具有指定識別碼之工作執行所在的執行緒。|  
|[GetVersion 方法](icordebugprocess2-getversion-method.md)|取得要在其上執行所要執行之進程的 CLR 版本。|  
|[SetDesiredNGENCompilerFlags 方法](icordebugprocess2-setdesiredngencompilerflags-method.md)|設定及時 (JIT) 編譯器所需的旗標，以將影像載入正在進行調試的進程。|  
|[SetUnmanagedBreakpoint 方法](icordebugprocess2-setunmanagedbreakpoint-method.md)|在指定的原生映射位移上設定未受管理的中斷點。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
