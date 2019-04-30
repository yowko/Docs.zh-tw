---
title: ICorProfilerCallback8::DynamicMethodJITCompilationFinished 方法
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9dbe8d4f7050b93ffb34280be6d63367ef294ae8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049709"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a>ICorProfilerCallback8::DynamicMethodJITCompilationFinished 方法
[.NET Framework 4.7 及更新版本中支援]  
  
通知分析工具，每當完成動態方法的 JIT 編譯。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
## <a name="parameters"></a>參數  
[in] `functionId`  
記憶體中函式開始的 JIT 編譯的識別項。   

[in] `hrStatus`   
值，指出 JIT 編譯是否成功。

[in] `fIsSafeToBlock`   
`true` 表示封鎖可能會導致執行階段，等候要從此回呼; 傳回呼叫的執行緒`false`表示封鎖會不會影響執行階段的作業。  

## <a name="remarks"></a>備註  

JIT 編譯的動態方法已完成時會觸發此回呼。 這包括各種 IL 虛設常式和 LCG 方法。 其目的在於提供足夠的資訊來識別使用者的已編譯的方法的程式碼剖析工具寫入器。

> [!NOTE]
> `functionId` 無法解析為其中繼資料語彙基元中，使用值，因為動態方法有沒有中繼資料。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [DynamicMethodJITCompilationStarted 方法](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [ICorProfilerCallback8 介面](icorprofilercallback8-interface.md)
