---
title: ICorProfiler回檔8：:DynamicMethodJIT編譯完成方法
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: c2e9489654a0fe5fa65ec638ed0f991a6c01415a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175105"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a>ICorProfiler回檔8：:DynamicMethodJIT編譯完成方法
[在 .NET 框架 4.7 和更高版本中支援]  
  
每當動態方法的 JIT 編譯完成時，通知探測器。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,
     [in]  BOOL        hrStatus,
     [in]  BOOL        fIsSafeToBlock
);  
```  
  
## <a name="parameters"></a>參數  
[in] `functionId`  
啟動 JIT 編譯的記憶體中函數的識別碼。

[在]`hrStatus`指示 JIT 編譯是否成功的值。

[在]`fIsSafeToBlock`指示阻塞可能導致運行時等待調用執行緒從此回檔
`true`返回;`false`指示阻塞不會影響運行時的操作。  

## <a name="remarks"></a>備註  

每當動態方法的 JIT 編譯完成時，都會觸發此回檔。 這包括各種 IL 存根和 LCG 方法。 其目的是向探測器編寫器提供足夠的資訊，以便向使用者標識編譯的方法。

> [!NOTE]
> `functionId`值不能用於解析到其中繼資料權杖，因為動態方法沒有中繼資料。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [DynamicMethodJITCompilationStarted 方法](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [ICorProfilerCallback8 介面](icorprofilercallback8-interface.md)
