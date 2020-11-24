---
title: ICorProfilerInfo::BeginInprocDebugging 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.BeginInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::BeginInprocDebugging
helpviewer_keywords:
- BeginInprocDebugging method [.NET Framework profiling]
- ICorProfilerInfo::BeginInprocDebugging method [.NET Framework profiling]
ms.assetid: c5c82c69-99f8-4447-aee0-42cca0a5eb5c
topic_type:
- apiref
ms.openlocfilehash: 3f56c3faa10eb05896936a37b0094797b0b6e2b9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95669168"
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a>ICorProfilerInfo::BeginInprocDebugging 方法

初始化同進程的偵錯工具支援。 此方法在 .NET Framework 版本2.0 中已淘汰。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
## <a name="parameters"></a>參數  

 `fThisThreadOnly`  
 在將此值設定為，就 `true` 只初始化目前線程的偵錯工具支援; 將它設定為， `false` 以初始化所有線程的偵錯工具支援。  
  
 `pdwProfilerContext`  
 擴展傳回值的指標，此值會識別偵錯工具會話。  
  
## <a name="remarks"></a>備註  

 CLR 偵錯工具在 .NET Framework 1.0 和1.1 版中支援有限的進程內進行中的偵錯工具。 同進程的偵錯工具可讓分析工具使用偵錯工具 API 的檢查部分。 不過，由於客戶的意見反應，已從2.0 版的 .NET Framework 中移除同進程的偵錯工具，並以一組與分析 API 更配合的功能來取代。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：** 1。0  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
