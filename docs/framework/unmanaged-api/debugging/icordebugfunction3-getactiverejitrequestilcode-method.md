---
title: ICorDebugFunction3::GetActiveReJitRequestILCode 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugFunction3.GetActiveReJitRequestILCode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 88584574-ade5-45b2-9778-489ed5c4dd7f
topic_type:
- apiref
ms.openlocfilehash: 7ab5f8826da0b38fc9f92d9be955991a88d15f69
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695994"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a>ICorDebugFunction3::GetActiveReJitRequestILCode 方法

[.NET Framework 4.5.2 與更新版本提供支援]  
  
 從使用中的 ReJIT 要求取得包含 IL 的 [ICorDebugILCode](icordebugilcode-interface.md) 介面指標。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
## <a name="parameters"></a>參數  

 `ppReJitedILCode`  
 作用中 ReJIT 要求之 IL 的指標。  
  
## <a name="remarks"></a>備註  

 如果此 `ICorDebugFunction3` 物件所代表的方法具有作用中 ReJIT 要求，則 `ppReJitedILCode` 會傳回其 IL 的指標。 如果沒有作用中的要求，這是常見的情況，則 `ppReJitedILCode` 為 **null**。  
  
 當執行從 [ICorProfilerCallback4：： GetReJITParameters](../profiling/icorprofilercallback4-getrejitparameters-method.md) 方法呼叫傳回之後，ReJIT 要求就會變成作用中狀態。 該要求可能未經 JIT 編譯，而執行緒可能仍在原始版本程式碼中執行。 在分析工具的 [ICorProfilerInfo4：： RequestRevert](../profiling/icorprofilerinfo4-requestrevert-method.md) 方法呼叫期間，ReJIT 要求變成非使用中。 即使在 IL 還原之後，執行緒仍可在 JIT 重新編譯的 (ReJIT) 程式碼中執行。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugFunction3 介面](icordebugfunction3-interface.md)
- [偵錯介面](debugging-interfaces.md)
- [ReJIT： How-To 指南](/archive/blogs/davbr/rejit-a-how-to-guide)
