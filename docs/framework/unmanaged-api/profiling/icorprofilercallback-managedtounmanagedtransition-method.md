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
ms.openlocfilehash: f4f5871bdd7adf11fcc811fd40c62e3027b8e607
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426183"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a>ICorProfilerCallback::ManagedToUnmanagedTransition 方法
通知分析工具，已發生從 managed 程式碼到未受管理程式碼的轉換。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a>參數  
 `functionId`  
 在所呼叫之函式的識別碼。  
  
 `reason`  
 在[COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)列舉的值，指出轉換是否因為從 managed 程式碼呼叫非受控碼而發生，或是因為非受控函式所呼叫的 managed 函數傳回。  
  
## <a name="remarks"></a>備註  
 如果 `reason` 的值為 COR_PRF_TRANSITION_CALL，則函式識別碼就是不會使用即時編譯器編譯的非受控函式。 非受控函式具有與其相關聯的基本資訊，例如名稱和一些中繼資料。 如果使用隱含平台叫用（PInvoke）呼叫了非受控函式，執行時間就無法判斷呼叫的目的地，而 `functionId` 的值將會是 null。 如需隱含 PInvoke 的詳細資訊，請參閱[使用C++ Interop （隱含 pinvoke）](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [UnmanagedToManagedTransition 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)
- [在 C++ 中使用明確的 PInvoke (DllImport 屬性)](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
