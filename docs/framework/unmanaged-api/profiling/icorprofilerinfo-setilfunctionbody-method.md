---
title: ICorProfilerInfo::SetILFunctionBody 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerInfo::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method [.NET Framework profiling]
ms.assetid: b159c712-00f4-4fc7-a990-40bf9f642e8f
topic_type:
- apiref
ms.openlocfilehash: 462fc7222243f8cad4e1d03d1717eedace549836
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502934"
---
# <a name="icorprofilerinfosetilfunctionbody-method"></a>ICorProfilerInfo::SetILFunctionBody 方法
取代指定模組中所指定函式的主體。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodid,  
    [in] LPCBYTE     pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a>參數  
 `moduleId`  
 在函數所在模組的識別碼。  
  
 `methodid`  
 在要取代主體之函式的 token。  
  
 `pbNewILMethodHeader`  
 在函數的新標頭。  
  
## <a name="remarks"></a>備註  
 `SetILFunctionBody`方法會取代中繼資料中函數的相對虛擬位址，使其指向新的函式主體，並視需要調整任何內部資料結構。  
  
 `SetILFunctionBody`只能在從未由即時（JIT）編譯器編譯的函式上呼叫方法。  
  
 使用[ICorProfilerInfo：： GetILFunctionBodyAllocator](icorprofilerinfo-getilfunctionbodyallocator-method.md)方法來配置新方法的空間，以確保緩衝區相容。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
