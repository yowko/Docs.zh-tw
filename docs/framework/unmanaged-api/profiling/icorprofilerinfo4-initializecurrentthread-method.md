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
ms.openlocfilehash: 51f16523c00cc3dd95b786f1586ccfd75ce8d5f1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733824"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a>ICorProfilerInfo4::InitializeCurrentThread 方法

在相同執行緒上的後續分析工具 API 呼叫之前，初始化目前的執行緒，因此可以避免鎖死。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a>備註  

 建議您 `InitializeCurrentThread` 在有暫止的執行緒時，于任何將呼叫 PROFILER API 的執行緒上呼叫。 這種方法通常是由取樣分析工具所使用，它會建立自己的執行緒來呼叫 [ICorProfilerInfo2：:D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md) 方法，以便在目標執行緒暫停時執行堆疊的逐步解說。 藉由在分析工具 `InitializeCurrentThread` 第一次建立取樣執行緒時呼叫一次，分析工具可以確定在第一次呼叫期間，CLR 會以其他方式執行的延遲個別執行緒初始化， `DoStackSnapshot` 現在可以在沒有其他執行緒暫止時安全地發生。  
  
> [!NOTE]
> `InitializeCurrentThread` 會事先進行初始化以完成可鎖定的工作，而且可能會發生鎖死。 `InitializeCurrentThread`只有在沒有暫止的執行緒時呼叫。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo4 介面](icorprofilerinfo4-interface.md)
- [分析介面](profiling-interfaces.md)
- [程式碼剖析](index.md)
