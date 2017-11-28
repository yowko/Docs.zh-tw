---
title: "FunctionEnter3WithInfo 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionEnter3WithInfo
api_location: mscorwks.cll
api_type: COM
f1_keywords: FunctionEnter3WithInfo
helpviewer_keywords: FunctionEnter3WithInfo function [.NET Framework profiling]
ms.assetid: 277c3344-d0cb-431e-beae-eb1eeeba8eea
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 37cdf823cc910dd1cebcb587d2616406a842fef2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="functionenter3withinfo-function"></a>FunctionEnter3WithInfo 函式
通知分析工具，控制權會被傳遞給函式，並提供的控制代碼，可以傳遞至[icorprofilerinfo3:: Getfunctionenter3info 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)擷取的堆疊框架和函式引數。  
  
## <a name="syntax"></a>語法  
  
```  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
#### <a name="parameters"></a>參數  
 `functionIDOrClientID`  
 [in]控制權會傳遞函式的識別項。  
  
 `eltInfo`  
 [in] 代表特定堆疊框架之資訊的不透明控制代碼。 這個控制代碼無效，只在它所傳遞的回呼。  
  
## <a name="remarks"></a>備註  
 `FunctionEnter3WithInfo`回呼方法會通知分析工具函式呼叫，並可讓分析工具使用[icorprofilerinfo3:: Getfunctionenter3info 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)檢查引數的值。 若要存取引數的詳細資訊，`COR_PRF_ENABLE_FUNCTION_ARGS`旗標必須設定。 分析工具可以使用[icorprofilerinfo:: Seteventmask 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)來設定事件的旗標，然後使用[icorprofilerinfo3:: Setenterleavefunctionhooks3withinfo 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)註冊您此函式實作。  
  
 `FunctionEnter3WithInfo`函式是回呼，您必須實作它。 實作必須使用`__declspec(naked)`儲存類別屬性。  
  
 執行引擎不會呼叫此函數之前儲存任何暫存器。  
  
-   進入時，您必須儲存所有您使用，包括浮點數的單位 (FPU) 中的暫存器。  
  
-   結束時，您必須還原堆疊取出關閉推入其呼叫端的所有參數。  
  
 實作`FunctionEnter3WithInfo`不應該封鎖，因為它將會延遲記憶體回收。 實作不應嘗試回收，因為堆疊可能不在記憶體回收方便集合的狀態。 如果嘗試在記憶體回收時，執行階段將會封鎖直到`FunctionEnter3WithInfo`傳回。  
  
 `FunctionEnter3WithInfo`函式不能呼叫 managed 程式碼或以任何方式導致受管理的記憶體配置。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [GetFunctionEnter3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)  
 [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [分析全域靜態函式](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
