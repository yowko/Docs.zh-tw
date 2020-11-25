---
title: ICorProfilerCallback::UnmanagedToManagedTransition 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.UnmanagedToManagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition
helpviewer_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition method [.NET Framework profiling]
- UnmanagedToManagedTransition method [.NET Framework profiling]
ms.assetid: ade2cc01-9b81-4e09-a5f9-b3b9dda27e96
topic_type:
- apiref
ms.openlocfilehash: 446de663d437c950f3a9be968e7dcbe8d25ed2b0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717228"
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a>ICorProfilerCallback::UnmanagedToManagedTransition 方法

通知分析工具，從非受控程式碼轉換成 managed 程式碼時發生。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a>參數  

 `functionId`  
 在正在呼叫之函式的識別碼。  
  
 `reason`  
 在 [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) 列舉值，這個值會指出是否因為從非受控程式碼的 managed 程式碼呼叫，或由 managed 函式所呼叫的非受控函式傳回而發生轉換。  
  
## <a name="remarks"></a>備註  

 如果的值 `reason` 是 COR_PRF_TRANSITION_RETURN 而不 `functionId` 是 null，則函式識別碼就是非受控函式的識別碼，而且永遠不會使用即時 (JIT) 編譯器進行編譯。 非受控函式有一些相關聯的基本資訊，例如名稱和一些中繼資料。  
  
 如果的值 `reason` 是 COR_PRF_TRANSITION_CALL，則呼叫的函式可能會 (也可能是 managed 函式) 尚未 JIT 編譯。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [ManagedToUnmanagedTransition 方法](icorprofilercallback-managedtounmanagedtransition-method.md)
- [在 c + + 中使用明確的 PInvoke (DllImport 屬性) ](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
- [使用 c + + Interop (隱含 PInvoke) ](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
