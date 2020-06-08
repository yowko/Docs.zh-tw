---
title: ICorProfilerInfo4::InitializeCurrentThread 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4::InitializeCurrentThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::InitializeCurrentThread
helpviewer_keywords:
- ICorProfilerInfo4::InitializeCurrentThread method [.NET Framework profiling]
- InitializeCurrentThread method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 18a3335c-8c75-476c-b6de-72c0bfedae5d
topic_type:
- apiref
ms.openlocfilehash: 1f3ff3e9b68aa30f424f4b2fe6c7cacd2cddd544
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495927"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a>ICorProfilerInfo4::InitializeCurrentThread 方法
在同一個執行緒上的後續分析工具 API 呼叫之前，將目前的執行緒初始化，以便避免鎖死。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a>備註  
 我們建議您在有 `InitializeCurrentThread` 擱置的執行緒時，于任何將呼叫分析工具 API 的執行緒上呼叫。 這個方法通常是由取樣分析工具所使用，它會建立自己的執行緒來呼叫[ICorProfilerInfo2：:D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md)方法，以便在目標執行緒暫停時執行堆疊的逐步解說。 藉由在分析工具 `InitializeCurrentThread` 第一次建立取樣執行緒時呼叫一次，分析工具可以確保在第一次呼叫時，CLR 原本就會執行的延遲每一線程初始化，現在會在 `DoStackSnapshot` 沒有其他執行緒暫停時安全地進行。  
  
> [!NOTE]
> `InitializeCurrentThread`會事先進行初始化，以完成會產生鎖定的工作，而且可能會鎖死。 `InitializeCurrentThread`只有在沒有暫止的執行緒時，才呼叫。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo4 介面](icorprofilerinfo4-interface.md)
- [分析介面](profiling-interfaces.md)
- [程式碼剖析](index.md)
