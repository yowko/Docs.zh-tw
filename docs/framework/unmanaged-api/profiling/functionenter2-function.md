---
title: FunctionEnter2 函式
ms.date: 03/30/2017
api_name:
- FunctionEnter2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter2
helpviewer_keywords:
- FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type:
- apiref
ms.openlocfilehash: 9aeb7a294beb10f9c2968e6161c72fdc362c4991
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177055"
---
# <a name="functionenter2-function"></a>FunctionEnter2 函式
通知探測器控制項正在傳遞到函數，並提供有關堆疊幀和函數參數的資訊。 此函數取代[函數Enter](functionenter-function.md)函數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,
    [in]  UINT_PTR                         clientData,
    [in]  COR_PRF_FRAME_INFO               func,
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a>參數

- `funcId`

  \[in] 傳遞給控制項的函數的識別碼。

- `clientData`

  \[in] 重新映射的函數識別碼，探測器以前使用[函數 IDMapper](functionidmapper-function.md)函數指定該識別碼。
  
- `func`

  \[in]`COR_PRF_FRAME_INFO`指向有關堆疊幀的資訊的值。
  
  探測器應將此視為不透明控制碼，可在[ICorProfilerInfo2 中傳回執行引擎：：get功能Info2](icorprofilerinfo2-getfunctioninfo2-method.md)方法。  
  
- `argumentInfo`

  \[in] 指向[COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md)結構的指標，用於指定函數參數的記憶體中的位置。

  為了訪問參數資訊，`COR_PRF_ENABLE_FUNCTION_ARGS`必須設置標誌。 探測器可以使用[ICorProfilerInfo：：SetEventMask](icorprofilerinfo-seteventmask-method.md)方法設置事件標誌。

## <a name="remarks"></a>備註  
 `func`和`argumentInfo`參數的值在`FunctionEnter2`函數返回後無效，因為值可能會更改或被銷毀。  
  
 函數`FunctionEnter2`是回檔;你必須實現它。 實現必須使用`__declspec`（`naked`） 存儲類屬性。  
  
 在調用此函數之前，執行引擎不會保存任何寄存器。  
  
- 進入時，必須保存您使用的所有寄存器，包括浮點單元 （FPU） 中的寄存器。  
  
- 在退出時，必須通過彈出其調用方推送的所有參數來還原堆疊。  
  
 的實現不應`FunctionEnter2`阻塞，因為它將延遲垃圾回收。 實現不應嘗試垃圾回收，因為堆疊可能未處於垃圾回收友好狀態。 如果嘗試垃圾回收，運行時將阻塞，直到`FunctionEnter2`返回。  
  
 此外，`FunctionEnter2`該函數不得調用託管代碼，或以任何方式導致託管記憶體分配。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾普羅普.伊德爾  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [FunctionLeave2 函式](functionleave2-function.md)
- [FunctionTailcall2 函式](functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2 方法](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [分析全域靜態函式](profiling-global-static-functions.md)
