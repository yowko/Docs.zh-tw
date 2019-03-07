---
title: ICorProfilerCallback8::DynamicMethodJITCompilationStarted 方法
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 170d0b20069724a4e1845be0250b2897daa10dee
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501236"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a>ICorProfilerCallback8::DynamicMethodJITCompilationStarted 方法
[.NET Framework 4.7 及更新版本中支援]  
  
已啟動的動態方法的 JIT 編譯時，請通知分析工具。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        fIsSafeToBlock,   
     [in]  LPCBYTE     pILHeader,   
     [in]  LONG        cbILHeader   
);  
```  
  
## <a name="parameters"></a>參數  
[in] `functionId`  
記憶體中函式開始的 JIT 編譯的識別項。   

[in] `fIsSafeToBlock`   
`true` 表示封鎖可能會導致執行階段，等候要從此回呼; 傳回呼叫的執行緒`false`表示封鎖會不會影響執行階段的作業。  

[in] `pILHeader`    
方法的 IL 標頭的第一個位元組指標。   

[in] `cbILHeader`    
IL 標頭中的位元組數目。 

## <a name="remarks"></a>備註  

動態方法可讓您在 JIT 編譯時，就會觸發此回呼。 這包括各種 IL 虛設常式和 LCG 方法。 其目的在於提供足夠的資訊來識別使用者的已編譯的方法的程式碼剖析工具寫入器。

> [!NOTE]
> `functionId` 無法解析為其中繼資料語彙基元中，使用值，因為動態方法有沒有中繼資料。

`pILHeader`指標才會有效的回呼期間。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>另請參閱
- [DynamicMethodJITCompilationFinished 方法](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [ICorProfilerCallback8 介面](icorprofilercallback8-interface.md)
