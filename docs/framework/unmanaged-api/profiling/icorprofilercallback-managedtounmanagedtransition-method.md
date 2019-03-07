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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 84ba3996d91d0e8a6bbf9cb1071a37909f2ee16d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484910"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a>ICorProfilerCallback::ManagedToUnmanagedTransition 方法
通知發生從 managed 程式碼轉換到 unmanaged 程式碼分析工具。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a>參數  
 `functionId`  
 [in]正在呼叫函式的識別碼。  
  
 `reason`  
 [in]值為[COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)列舉，指出轉換是否發生因為呼叫 unmanaged 程式碼從 managed 程式碼，或因為由未受管理的一個呼叫 managed 函式傳回。  
  
## <a name="remarks"></a>備註  
 如果值`reason`是 COR_PRF_TRANSITION_CALL，識別碼是，unmanaged 的函式，將永遠不會已編譯使用-just-in-time 編譯器函式。 Unmanaged 函式有與其相關聯，例如名稱及一些中繼資料的基本資訊。 如果 unmanaged 函式呼叫使用隱含的平台叫用 (PInvoke)，執行階段無法判斷呼叫的目的地，而`functionId`將會是 null。 如需有關隱含 PInvoke 的詳細資訊，請參閱 <<c0> [ 使用 c + + Interop (隱含 PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [UnmanagedToManagedTransition 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)
- [在 C++ 中使用明確的 PInvoke (DllImport 屬性)](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
