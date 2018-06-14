---
title: FunctionIDMapper 函式
ms.date: 03/30/2017
api_name:
- FunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper
helpviewer_keywords:
- FunctionIDMapper function [.NET Framework profiling]
ms.assetid: b8205b60-1893-4303-8cff-7ac5a00892aa
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 151b790afaf6a251ba5d8d8932f44a503cde853a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458594"
---
# <a name="functionidmapper-function"></a>FunctionIDMapper 函式
通知分析工具函式的指定的識別碼可能會重新對應至替代識別碼，以用於[FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)， [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)，和[FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)該函式的回呼。 `FunctionIDMapper` 也可讓分析工具指出它是否要接收該函式的回呼。  
  
## <a name="syntax"></a>語法  
  
```  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
#### <a name="parameters"></a>參數  
 `funcId`  
 [in] 要重新對應的函式識別項。  
  
 `pbHookFunction`  
 [out]分析工具會設定為值的指標`true`如果它要接收`FunctionEnter2`， `FunctionLeave2`，和`FunctionTailcall2`回呼; 否則它將此值設`false`。  
  
## <a name="return-value"></a>傳回值  
 分析工具會傳回一個值，執行引擎會使用該值做為替代函式識別項。 傳回值不可為 null，除非 `false` 傳回在 `pbHookFunction` 中。 否則，傳回的 null 值會產生無法預期的結果，包括可能暫止處理程序。  
  
## <a name="remarks"></a>備註  
 `FunctionIDMapper`函式是回呼。 它是由某些其他識別碼，程式碼剖析工具更有用的函式識別碼重新對應的程式碼剖析工具實作。 `FunctionIDMapper`傳回要用於指定的函式的替代 ID。 執行引擎藉由傳遞回程式碼剖析工具中的這個替代識別碼，除了傳統的函式 ID，然後接受分析工具的要求`clientData`參數`FunctionEnter2`， `FunctionLeave2`，和`FunctionTailcall2`攔截程序，來識別正在呼叫攔截函式。  
  
 您可以使用[icorprofilerinfo:: Setfunctionidmapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)方法，以指定的實作`FunctionIDMapper`函式。 您可以呼叫`ICorProfilerInfo::SetFunctionIDMapper`方法一次，所以我們建議，請在[icorprofilercallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)回呼。  
  
 根據預設，它會假設，分析工具，設定 COR_PRF_MONITOR_ENTERLEAVE 旗標使用[icorprofilerinfo:: Seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)，它會設定攔截程序，透過和[icorprofilerinfo:: Setenterleavefunctionhooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md)或[icorprofilerinfo2:: Setenterleavefunctionhooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)，應該會收到`FunctionEnter2`， `FunctionLeave2`，和`FunctionTailcall2`每個函式的回呼。 不過，分析工具可能會實作`FunctionIDMapper`以選擇性地避免特定接收這些回呼函式藉由設定`pbHookFunction`至`false`。  
  
 程式碼剖析工具應該分析應用程式的多個執行緒所呼叫同時相同的方法/函式的情況下容錯。 在這種情況下，分析工具可能會收到多個`FunctionIDMapper`相同的回呼`FunctionID`。 程式碼剖析工具應該先確定要從此回呼傳回相同的值，多次呼叫具有相同時`FunctionID`。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [SetFunctionIDMapper 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [FunctionIDMapper2 函式](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)  
 [FunctionEnter2 函式](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [FunctionLeave2 函式](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [FunctionTailcall2 函式](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [分析全域靜態函式](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
