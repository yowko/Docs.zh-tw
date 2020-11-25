---
title: ICorProfilerCallback::ManagedToUnmanagedTransition 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ManagedToUnmanagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ManagedToUnmanagedTransition
helpviewer_keywords:
- ManagedToUnmanagedTransition method [.NET Framework profiling]
- ICorProfilerCallback::ManagedToUnmanagedTransition method [.NET Framework profiling]
ms.assetid: ef3cd619-912d-40c5-a449-03ba02a39ee7
topic_type:
- apiref
ms.openlocfilehash: ef65ed908c71bcc2755aaf42070439fd7dab3f6d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733135"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a>ICorProfilerCallback::ManagedToUnmanagedTransition 方法

通知分析工具將 managed 程式碼轉換為非受控程式碼時發生。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a>參數  

 `functionId`  
 在正在呼叫之函式的識別碼。  
  
 `reason`  
 在 [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) 列舉值，這個值會指出是否因為從 managed 程式碼呼叫非受控碼，或從非受控函式所呼叫的 managed 函式傳回，而發生轉換。  
  
## <a name="remarks"></a>備註  

 如果的值 `reason` 是 COR_PRF_TRANSITION_CALL，則函式識別碼就是非受控函式的識別碼，該函式不會使用即時編譯器進行編譯。 非受控函式有與其相關聯的基本資訊，例如名稱和一些中繼資料。 如果使用隱含平台叫用呼叫非受控函式 (PInvoke) ，則執行時間無法判斷呼叫的目的地，而的值將會 `functionId` 是 null。 如需隱含 PInvoke 的詳細資訊，請參閱 [使用 c + + Interop (隱含的 pinvoke) ](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [UnmanagedToManagedTransition 方法](icorprofilercallback-unmanagedtomanagedtransition-method.md)
- [在 c + + 中使用明確的 PInvoke (DllImport 屬性) ](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
