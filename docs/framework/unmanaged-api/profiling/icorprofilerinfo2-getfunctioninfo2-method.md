---
title: "ICorProfilerInfo2::GetFunctionInfo2 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetFunctionInfo2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetFunctionInfo2
helpviewer_keywords:
- GetFunctionInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetFunctionInfo2 method [.NET Framework profiling]
ms.assetid: 0aa60f24-8bbd-4c83-83c5-86ad191b1d82
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e7a48f109c22ae768e636a7f6b57e4e10ac76012
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a>ICorProfilerInfo2::GetFunctionInfo2 方法
取得函式的父類別、中繼資料語彙基元和每個類型引數的 `ClassID` (如果有的話)。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetFunctionInfo2(  
    [in]  FunctionID funcId,  
    [in]  COR_PRF_FRAME_INFO frameInfo,  
    [out] ClassID *pClassId,  
    [out] ModuleID *pModuleId,  
    [out] mdToken *pToken,  
    [in]  ULONG32 cTypeArgs,  
    [out] ULONG32 *pcTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
#### <a name="parameters"></a>參數  
 `funcId`  
 [in] 用來取得父類別和其他資訊的函式 ID。  
  
 `frameInfo`  
 [in] 指向堆疊框架相關資訊的 `COR_PRF_FRAME_INFO` 值。  
  
 `pClassId`  
 [out] 函式父類別的指標。  
  
 `pModuleId`  
 [out] 定義函式父類別的模組指標。  
  
 `pToken`  
 [out] 此函式中繼資料語彙基元的指標。  
  
 `cTypeArgs`  
 [in] `typeArgs` 陣列的大小。  
  
 `pcTypeArgs`  
 [out] `ClassID` 值總數的指標。  
  
 `typeArgs`  
 [out] 一組 `ClassID`  值的陣列，其中每一項為該函式類型引數的 ID。 方法傳回時， `typeArgs` 將包含部分或所有的 `ClassID` 值。  
  
## <a name="remarks"></a>備註  
 分析工具程式碼可以呼叫[icorprofilerinfo:: Getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)取得[中繼資料](../../../../docs/framework/unmanaged-api/metadata/index.md)提供之模組的介面。 然後，傳回至 `pToken` 所參考位置的中繼資料語彙基元可以用來存取此函式的中繼資料。  
  
 透過 `pClassId` 和 `typeArgs` 參數傳回的類別 ID 與類型引數取決於在 `frameInfo` 參數中傳遞的值，如下表所示。  
  
|`frameInfo` 參數的值|結果|  
|----------------------------------------|------------|  
|從 `COR_PRF_FRAME_INFO` 回呼取得的 `FunctionEnter2` 值|在 `pClassId` 所參考位置中傳回的 `ClassID` 和 `typeArgs` 陣列傳回的所有類型引數，都會是精確的。|  
|從 `FunctionEnter2` 回呼以外來源取得的 `COR_PRF_FRAME_INFO`。|無法決定精確的 `ClassID` 和類型引數。 也就是說，`ClassID` 可能是 null，而且可能會有某些類型引數做為 <xref:System.Object> 傳回。|  
|零|無法決定精確的 `ClassID` 和類型引數。 也就是說，`ClassID` 可能是 null，而且可能會傳回某些類型引數做為 <xref:System.Object>。|  
  
 `GetFunctionInfo2` 傳回之後，您必須確認 `typeArgs` 緩衝區夠大，以包含所有 `ClassID` 的值。 若要這樣做，請比對 `pcTypeArgs` 指向的值和 `cTypeArgs` 參數。 如果 `pcTypeArgs` 指向一個值，該值大於 `cTypeArgs` 除以 `ClassID` 值的大小，請配置較大的 `pcTypeArgs` 緩衝區，以新的、較大的大小來更新 `cTypeArgs`，然後再呼叫 `GetFunctionInfo2` 一次。  
  
 此外，您可以先使用長度為零的 `pcTypeArgs` 緩衝區來呼叫 `GetFunctionInfo2`，以取得正確的緩衝區大小。 您可以將緩衝區大小設定為 `pcTypeArgs` 傳回的值除以 `ClassID` 值的大小，然後再呼叫 `GetFunctionInfo2` 一次。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [程式碼剖析](../../../../docs/framework/unmanaged-api/profiling/index.md)
