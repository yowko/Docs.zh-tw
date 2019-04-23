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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f12442eb5596ff3dca49cf24e27040f3e92d3a7c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072606"
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a>ICorProfilerInfo::BeginInprocDebugging 方法
初始化同處理序偵錯支援。 這個方法是在.NET Framework 2.0 版中已過時。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
## <a name="parameters"></a>參數  
 `fThisThreadOnly`  
 [in]將此值設定為`true`初始化偵錯的支援，只能在目前的執行緒; 將它設定為`false`初始化的所有執行緒的偵錯支援。  
  
 `pdwProfilerContext`  
 [out]要傳回的值，可識別偵錯工作階段的指標。  
  
## <a name="remarks"></a>備註  
 CLR 偵錯服務支援有限的處理序中的偵錯.NET framework 1.0 和 1.1 版。 若要使用偵錯 API 檢查部分的程式碼剖析工具啟用同處理序偵錯。 不過，由於客戶的意見反應，同處理序偵錯已移除從.NET Framework 2.0 版中，並取代為一組更符合程式碼剖析 API 的功能。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** 1.0  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
