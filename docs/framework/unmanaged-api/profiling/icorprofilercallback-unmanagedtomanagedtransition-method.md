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
ms.openlocfilehash: c381d4a85a1e836f1972060c8182dd698bb27550
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76870531"
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a>ICorProfilerCallback::UnmanagedToManagedTransition 方法
通知分析工具，已發生從非受控碼到 managed 程式碼的轉換。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a>參數  
 `functionId`  
 在所呼叫之函式的識別碼。  
  
 `reason`  
 在[COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md)列舉的值，指出轉換是因為來自非受控程式碼的 managed 程式碼呼叫，還是因為由 managed 函式所呼叫的非受控函數傳回而發生。  
  
## <a name="remarks"></a>備註  
 如果 `reason` 的值為 COR_PRF_TRANSITION_RETURN 且 `functionId` 不是 null，則函式識別碼會是非受控函式的 ID，而且永遠不會使用即時（JIT）編譯器來編譯。 非受控函式有一些與其相關聯的基本資訊，例如名稱和一些中繼資料。  
  
 如果 `reason` 的值為 COR_PRF_TRANSITION_CALL，則可能是被呼叫的函式（也就是 managed 函數）尚未進行 JIT 編譯。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [ManagedToUnmanagedTransition 方法](icorprofilercallback-managedtounmanagedtransition-method.md)
- [在 C++ 中使用明確的 PInvoke (DllImport 屬性)](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
- [使用 C++ Interop (隱含 PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
