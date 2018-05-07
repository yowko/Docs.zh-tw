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
ms.openlocfilehash: ad74eeb4deeae73be40b3a0bc0f6a18ec2299780
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a>ICorProfilerCallback8::DynamicMethodJITCompilationStarted 方法
[在.NET Framework 4.7 和更新版本中支援]  
  
動態方法的 JIT 編譯已啟動時，通知分析工具。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        fIsSafeToBlock,   
     [in]  LPCBYTE     pILHeader,   
     [in]  LONG        cbILHeader   
);  
```  
  
#### <a name="parameters"></a>參數  
[輸入] `functionId`  
記憶體中函式的 JIT 編譯為已啟動的識別項。   

[in] `fIsSafeToBlock`   
`true` 表示封鎖可能會造成執行階段從這個回呼; 傳回呼叫執行緒的等候`false`表示封鎖將不會影響執行階段的作業。  

[in] `pILHeader`    
方法的 IL 標頭的第一個位元組指標。   

[in] `cbILHeader`    
IL 標頭中的位元組數目。 

## <a name="remarks"></a>備註  

動態方法可讓您在 JIT 編譯時會觸發此回呼。 這包括各種 IL 虛設常式和 LCG 方法。 其目的在於提供足夠的資訊來識別使用者的已編譯的方法的程式碼剖析工具寫入器。

> [!NOTE]
> `functionId` 無法解析的中繼資料語彙基元，為使用值，因為動態方法沒有中繼資料。

`pILHeader`指標只適用於回呼期間。

## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>另請參閱  
 [DynamicMethodJITCompilationFinished 方法](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)  
 [ICorProfilerCallback8 介面](icorprofilercallback8-interface.md)
