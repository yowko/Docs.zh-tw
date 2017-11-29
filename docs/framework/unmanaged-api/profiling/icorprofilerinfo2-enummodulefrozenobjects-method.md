---
title: "ICorProfilerInfo2::EnumModuleFrozenObjects 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.EnumModuleFrozenObjects
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::EnumModuleFrozenObjects
helpviewer_keywords:
- EnumModuleFrozenObjects method [.NET Framework profiling]
- ICorProfilerInfo2::EnumModuleFrozenObjects method [.NET Framework profiling]
ms.assetid: 920b6483-7064-4d64-8613-fcc38ccf9b1e
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3214468045e98d83e2fb0f9c14c851abb45e217b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2enummodulefrozenobjects-method"></a>ICorProfilerInfo2::EnumModuleFrozenObjects 方法
取得允許反覆項目所指定模組中凍結物件的列舉值。這個方法已過時。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT EnumModuleFrozenObjects(  
    [in] ModuleID moduleID,  
    [out] ICorProfilerObjectEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>參數  
 `moduleID`  
 [in]包含要列舉的凍結的物件模組的識別碼。  
  
 `ppEnum`  
 [out]位址指標[ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)介面，其中會列舉凍結的物件。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** 3.5、 3.0 SP1、 3.0、 2.0 SP1、 2.0  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
