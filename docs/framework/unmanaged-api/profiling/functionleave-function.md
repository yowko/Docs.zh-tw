---
title: FunctionLeave 函式
ms.date: 03/30/2017
api_name:
- FunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave
helpviewer_keywords:
- FunctionLeave function [.NET Framework profiling]
ms.assetid: 18e89f45-e068-426a-be16-9f53a4346860
topic_type:
- apiref
ms.openlocfilehash: 13636da9c3e8ac4aa9e8dc1fa02b2e33afef4717
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722254"
---
# <a name="functionleave-function"></a>FunctionLeave 函式

通知分析工具，函式即將傳回到呼叫端。  
  
> [!NOTE]
> `FunctionLeave`函數在 .NET Framework 2.0 中已被取代。 它會繼續運作，但會導致效能下降。 請改用 [FunctionLeave2](functionleave2-function.md) 函數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a>參數

- `funcID`

  \[in] 傳回之函式的識別碼。

## <a name="remarks"></a>備註  

 `FunctionLeave`函數是回呼; 您必須加以執行。 實作為必須使用 `__declspec` (`naked`) 儲存類別屬性。  
  
 在呼叫此函式之前，執行引擎不會儲存任何暫存器。  
  
- 輸入時，您必須儲存使用的所有暫存器，包括浮點數單位中的所有暫存器 (FPU) 。  
  
- 在結束時，您必須藉由關閉呼叫端所推送的所有參數來還原堆疊。  
  
 的執行 `FunctionLeave` 不應封鎖，因為它會延遲垃圾收集。 執行不應嘗試垃圾收集，因為堆疊可能不是處於垃圾收集的易記狀態。 如果嘗試垃圾收集，則執行時間會封鎖直到傳回為止 `FunctionLeave` 。  
  
 此外，此函式 `FunctionLeave` 不能呼叫 managed 程式碼，或以任何方式造成受控記憶體配置。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corprof.h .idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：** 1.1、1。0  
  
## <a name="see-also"></a>另請參閱

- [FunctionEnter2 函式](functionenter2-function.md)
- [FunctionLeave2 函式](functionleave2-function.md)
- [FunctionTailcall2 函式](functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2 方法](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [分析全域靜態函式](profiling-global-static-functions.md)
