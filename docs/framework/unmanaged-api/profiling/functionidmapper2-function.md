---
title: FunctionIDMapper2 函式
ms.date: 03/30/2017
api_name:
- FunctionIDMapper2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper2
helpviewer_keywords:
- FunctionIDMapper2 function [.NET Framework profiling]
ms.assetid: 466ad51b-8f0c-41d9-81f7-371aac3374cb
topic_type:
- apiref
ms.openlocfilehash: af0ef412395394bb660ae6ed64fb154caef41655
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866914"
---
# <a name="functionidmapper2-function"></a>FunctionIDMapper2 函式
通知分析工具，函式的指定識別碼可能會重新對應到替代識別碼，以便用於[FunctionEnter3](functionenter3-function.md)、 [FunctionLeave3](functionleave3-function.md)和[FunctionTailcall3](functiontailcall3-function.md)，或[FunctionEnter3WithInfo](functionenter3withinfo-function.md)、 [FunctionLeave3WithInfo](functionleave3withinfo-function.md)和[FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)回呼（針對該函數）。 `FunctionIDMapper2` 也可讓分析工具指出它是否要接收該函式的回呼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper2 (  
    [in]  FunctionID  funcId,  
    [in]  void * clientData,  
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>參數

- `funcId`

  中的 \[] 要重新對應的函式識別碼。

- `clientData`

  \[in]）用來在執行時間之間區分的資料指標。

- `pbHookFunction`

  \[out] 值的指標，如果它想要接收 `FunctionEnter3`、`FunctionLeave3`和 `FunctionTailcall3`，或 `FunctionEnter3WithInfo`、`FunctionLeave3WithInfo`和 `FunctionTailcall3WithInfo` 回呼，則分析工具會將其設定為 `true`。否則，它會將此值設定為 `false`。

## <a name="return-value"></a>傳回值  
 分析工具會傳回一個值，執行引擎會使用該值做為替代函式識別項。 傳回值不可為 null，除非 `false` 傳回在 `pbHookFunction` 中。 否則，傳回的 null 值會產生無法預期的結果，包括可能暫止處理序。  
  
## <a name="remarks"></a>備註  
 這個方法會使用用來傳遞用戶端資料的額外參數來擴充[FunctionIDMapper](functionidmapper-function.md)函數。 用戶端資料會用來區分執行階段。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Corprof.idl .idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerInfo：： SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md)
- [ICorProfilerInfo3：： SetFunctionIDMapper2](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [FunctionEnter3](functionenter3-function.md)
- [FunctionLeave3](functionleave3-function.md)
- [FunctionTailcall3](functiontailcall3-function.md)
- [FunctionEnter3WithInfo](functionenter3withinfo-function.md)
- [FunctionLeave3WithInfo](functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)
- [分析全域靜態函式](profiling-global-static-functions.md)
