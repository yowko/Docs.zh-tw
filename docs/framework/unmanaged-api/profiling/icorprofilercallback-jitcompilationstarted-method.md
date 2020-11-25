---
title: ICorProfilerCallback::JITCompilationStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationStarted
helpviewer_keywords:
- JITCompilationStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationStarted method [.NET Framework profiling]
ms.assetid: 31782b36-d311-4518-8f45-25f65385af5b
topic_type:
- apiref
ms.openlocfilehash: 7ce100a68a3e2b8963ed14bbf044fa9ba11d629f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725510"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a>ICorProfilerCallback::JITCompilationStarted 方法

通知分析工具，及時 (JIT) 編譯器已開始編譯函式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>參數  

 `functionId`  
 在編譯開始的函式識別碼。  
  
 `fIsSafeToBlock`  
 在值，指出封鎖程式是否會影響執行時間的作業。 `true`如果封鎖可能會導致執行時間等候呼叫執行緒從此回呼傳回，則值為，否則為 `false` 。  
  
 雖然的值 `true` 不會危害執行時間，但它可能會扭曲分析結果。  
  
## <a name="remarks"></a>備註  

 由於執行時間處理類別的函式，因此您可以針對每個函式接收一對以上的 `JITCompilationStarted` [ICorProfilerCallback：： JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md) 呼叫。 例如，執行時間會開始 JIT 編譯方法 A，但必須執行類別 B 的類別函式。 因此，執行時間會 JIT 編譯類別 B 的函式並加以執行。 當函式執行時，它會呼叫方法 A，使方法 A 再次進行 JIT 編譯。 在此案例中，會暫停方法 A 的第一個 JIT 編譯。 不過，這兩個嘗試 JIT 編譯方法 A 的動作都會以 JIT 編譯事件來回報。 如果分析工具會藉由呼叫 [ICorProfilerInfo：： SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) 方法來取代方法 A 的 Microsoft 中繼語言 (MSIL) 程式碼，則這兩個事件都必須這麼做 `JITCompilationStarted` ，但它可能會對兩者使用相同的 MSIL 區塊。  
  
 如果兩個執行緒同時進行回呼，分析工具必須支援 JIT 回呼的順序。 例如，呼叫的執行緒 `JITCompilationStarted` 。 不過，在呼叫執行緒之前 `JITCompilationFinished` ，執行緒 B 會使用執行緒 a 回呼的函式識別碼呼叫 [ICorProfilerCallback：： ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) `JITCompilationStarted` 。 這可能會出現，因為分析工具尚未收到呼叫，所以函式識別碼應該尚未有效 `JITCompilationFinished` 。 不過，在這種情況下，函數識別碼是有效的。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [JITCompilationFinished 方法](icorprofilercallback-jitcompilationfinished-method.md)
