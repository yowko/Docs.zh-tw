---
title: "StackSnapshotCallback 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- StackSnapshotCallback
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- StackSnapshotCallback
helpviewer_keywords:
- StackSnapshotCallback function [.NET Framework profiling]
ms.assetid: d0f235b2-91fe-4f82-b7d5-e5c64186eea8
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 32cf21fb5a76fdec4daa322d53a8eb218ae2f2b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="stacksnapshotcallback-function"></a>StackSnapshotCallback 函式
提供程式碼剖析工具相關資訊每個 managed 的框架和每次執行未受管理的框架的堆疊上堆疊查核行程，由起始期間[icorprofilerinfo2:: Dostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT __stdcall StackSnapshotCallback (  
    [in] FunctionID funcId,  
    [in] UINT_PTR ip,  
    [in] COR_PRF_FRAME_INFO frameInfo,  
    [in] ULONG32 contextSize,  
    [in] BYTE context[],  
    [in] void *clientData  
);  
```  
  
#### <a name="parameters"></a>參數  
 `funcId`  
 [in]如果此值為零，這個回呼位於執行的未受管理的框架。否則，它是 managed 函式的識別碼，這個回呼位於個 managed 框架。  
  
 `ip`  
 [in]原生程式碼指令指標框架中的值。  
  
 `frameInfo`  
 [in]A`COR_PRF_FRAME_INFO`值所參考的堆疊框架的相關資訊。 只有在這個回呼期間，這個值可供使用。  
  
 `contextSize`  
 [in]大小`CONTEXT`結構，也就由參考`context`參數。  
  
 `context`  
 [in]對 win32 指標`CONTEXT`結構，表示這個畫面格 CPU 的狀態。  
  
 `context`參數是傳入 COR_PRF_SNAPSHOT_CONTEXT 旗標時，才有效`ICorProfilerInfo2::DoStackSnapshot`。  
  
 `clientData`  
 [in]用戶端資料，這直接透過傳遞指標`ICorProfilerInfo2::DoStackSnapshot`。  
  
## <a name="remarks"></a>備註  
 `StackSnapshotCallback`函式由程式碼剖析工具寫入器實作。 您必須限制在執行工作的複雜度`StackSnapshotCallback`。 例如，當使用`ICorProfilerInfo2::DoStackSnapshot`以非同步的方式，目標執行緒可能持有的鎖定。 如果內的程式碼`StackSnapshotCallback`需要相同的鎖定，可能發生死結。  
  
 `ICorProfilerInfo2::DoStackSnapshot`方法呼叫`StackSnapshotCallback`managed 框架每一次或一次每一回合的 unmanaged 框架的函式。 如果`StackSnapshotCallback`稱為 「 執行中的未受管理的框架，分析工具可能會使用暫存器內容 (所參考`context`參數) 來執行它自己的未受管理的堆疊查核行程。 在此情況下，Win32`CONTEXT`結構代表最近推送的框架內的未受管理的框架執行的 CPU 狀態。 雖然 Win32`CONTEXT`結構包含之所有暫存器值，則您應該只依賴的堆疊指標暫存器、 框架指標暫存器、 指令指標暫存器和靜態 （即保留） 值整數暫存器。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [DoStackSnapshot 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
 [分析全域靜態函式](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
