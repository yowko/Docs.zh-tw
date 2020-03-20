---
title: FunctionTailcall2 函式
ms.date: 03/30/2017
api_name:
- FunctionTailcall2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall2
helpviewer_keywords:
- FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type:
- apiref
ms.openlocfilehash: 60276327617ae24e9bdcebf958613c21d3808429
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175183"
---
# <a name="functiontailcall2-function"></a>FunctionTailcall2 函式
通知探測器當前執行的函數即將對另一個函數執行尾調用，並提供有關堆疊幀的資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,
    [in] UINT_PTR           clientData,
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a>參數

- `funcId`

  \[in] 即將進行尾調用的當前執行函數的識別碼。

- `clientData`

  \[in] 重新映射的函數識別碼，探測器以前通過函數[IDMapper](functionidmapper-function.md)指定，該識別碼是當前正在執行的函數，該函數即將進行尾調用。
  
- `func`

  \[in]`COR_PRF_FRAME_INFO`指向有關堆疊幀的資訊的值。

  探測器應將此視為不透明控制碼，可在[ICorProfilerInfo2 中傳回執行引擎：：get功能Info2](icorprofilerinfo2-getfunctioninfo2-method.md)方法。

## <a name="remarks"></a>備註  
 尾調用的目標函數將使用當前堆疊幀，並將直接返回到發出尾調用的函數的調用方。 這意味著不會為作為尾調用目標的函數發出[函數Leave2](functionleave2-function.md)回檔。  
  
 函數返回後`FunctionTailcall2`，`func`參數的值無效，因為該值可能會更改或銷毀。  
  
 函數`FunctionTailcall2`是回檔;你必須實現它。 實現必須使用`__declspec`（`naked`） 存儲類屬性。  
  
 在調用此函數之前，執行引擎不會保存任何寄存器。  
  
- 進入時，必須保存您使用的所有寄存器，包括浮點單元 （FPU） 中的寄存器。  
  
- 在退出時，必須通過彈出其調用方推送的所有參數來還原堆疊。  
  
 的實現不應`FunctionTailcall2`阻塞，因為它將延遲垃圾回收。 實現不應嘗試垃圾回收，因為堆疊可能未處於垃圾回收友好狀態。 如果嘗試垃圾回收，運行時將阻塞，直到`FunctionTailcall2`返回。  
  
 此外，`FunctionTailcall2`該函數不得調用託管代碼，或以任何方式導致託管記憶體分配。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾普羅普.伊德爾  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [FunctionEnter2 函式](functionenter2-function.md)
- [FunctionLeave2 函式](functionleave2-function.md)
- [SetEnterLeaveFunctionHooks2 方法](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [分析全域靜態函式](profiling-global-static-functions.md)
