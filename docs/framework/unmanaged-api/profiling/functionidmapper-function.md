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
ms.openlocfilehash: 0cf2014d7007593c51868eff0b488fdab136e362
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175170"
---
# <a name="functionidmapper-function"></a>FunctionIDMapper 函式
通知探測器，函數的給定識別碼可以重新映射到要用於該函數[的函數Enter2、](functionenter2-function.md)[函數Leave2](functionleave2-function.md)和[函數尾聲2](functiontailcall2-function.md)回檔中使用的替代 ID。 `FunctionIDMapper` 也可讓分析工具指出它是否要接收該函式的回呼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>參數

- `funcId`

  \[in] 要重新映射的函數識別碼。

- `pbHookFunction`

  \[out_ 指向探測器`true`在要接收`FunctionEnter2`時`FunctionLeave2`設置的值的指標， `FunctionTailcall2`否則，它將此值設置為`false`。

## <a name="return-value"></a>傳回值  
 分析工具會傳回一個值，執行引擎會使用該值做為替代函式識別項。 傳回值不可為 null，除非 `false` 傳回在 `pbHookFunction` 中。 否則，空傳回值將生成不可預知的結果，包括可能停止該過程。  
  
## <a name="remarks"></a>備註  
 該`FunctionIDMapper`函數是回檔。 探測器實現了它將函數 ID 重新映射到對探測器更有用的其他識別碼。 返回`FunctionIDMapper`用於任何給定函數的備用 ID。 然後，執行引擎通過將此備用 ID（除了傳統的函數`clientData`ID）傳遞給`FunctionEnter2`、`FunctionLeave2`和`FunctionTailcall2`掛鉤參數中的探測器來標識為其調用掛鉤的功能來回應探測器的請求。  
  
 您可以使用[ICorProfilerInfo：：Set功能IDMapper](icorprofilerinfo-setfunctionidmapper-method.md)方法來指定`FunctionIDMapper`函數的實現。 您只能調用該方法`ICorProfilerInfo::SetFunctionIDMapper`一次，我們建議您在[ICorProfiler 回檔：：初始化](icorprofilercallback-initialize-method.md)回檔中調用該方法。  
  
 預設情況下，假定使用[ICorProfilerInfo：：setEventMask](icorprofilerinfo-seteventmask-method.md)設置COR_PRF_MONITOR_ENTERLEAVE標誌的探測器，並且通過[ICorProfilerInfo 設置掛鉤：設置EnterLeave函數Hooks](icorprofilerinfo-setenterleavefunctionhooks-method.md)或[ICorProfilerInfo2：SetEnterLeave函數Hooks2，](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)應接收 每個函數的`FunctionEnter2`、`FunctionLeave2`和`FunctionTailcall2`回檔。 但是，探測器可以通過`FunctionIDMapper`設置為`pbHookFunction`有選擇地避免接收某些函數的回檔`false`。  
  
 探測器應容忍設定檔應用程式的多個執行緒同時調用同一方法/函數的情況。 在這種情況下，探測器可能會收到同`FunctionIDMapper``FunctionID`一的多個回檔。 當同調用多次回檔時，探測器應確定應從此回檔返回相同的`FunctionID`值。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾普羅普.伊德爾  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [SetFunctionIDMapper 方法](icorprofilerinfo-setfunctionidmapper-method.md)
- [FunctionIDMapper2 函式](functionidmapper2-function.md)
- [FunctionEnter2 函式](functionenter2-function.md)
- [FunctionLeave2 函式](functionleave2-function.md)
- [FunctionTailcall2 函式](functiontailcall2-function.md)
- [分析全域靜態函式](profiling-global-static-functions.md)
