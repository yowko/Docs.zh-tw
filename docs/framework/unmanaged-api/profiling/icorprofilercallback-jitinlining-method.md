---
title: ICorProfilerCallback::JITInlining 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITInlining
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITInlining
helpviewer_keywords:
- JITInlining method [.NET Framework profiling]
- ICorProfilerCallback::JITInlining method [.NET Framework profiling]
ms.assetid: c2f45801-dd38-4b78-b6b7-64397dc73f83
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 844ac2a8aad4ce2cc6f70de2d5a53c7c0b6f4f6c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackjitinlining-method"></a>ICorProfilerCallback::JITInlining 方法
通知分析工具在 just-in-time (JIT) 編譯器即將插入與另一個函式的函式。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
#### <a name="parameters"></a>參數  
 `callerId`  
 [in]所在的函式 ID`calleeId`函式將會插入。  
  
 `calleeId`  
 [in]要插入的函式 ID。  
  
 `pfShouldInline`  
 [out]`true`允許插入發生; 否則`false`。  
  
## <a name="remarks"></a>備註  
 分析工具可以設定`pfShouldInline`至`false`防止`calleeId`函式插入`callerId`函式。 此外，分析工具可以全域使用停用內嵌插入 COR_PRF_DISABLE_INLINING 值[COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列舉型別。  
  
 內嵌函式插入不會引發事件進入或離開。 因此，必須設定程式碼剖析工具`pfShouldInline`至`false`才能產生精確範圍的 callgraph。 設定`pfShouldInline`至`false`會影響效能，因為內嵌插入通常會提升速度和減少插入的方法不同的 JIT 編譯事件。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
