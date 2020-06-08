---
title: ICorProfilerInfo::GetILFunctionBodyAllocator 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBodyAllocator
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBodyAllocator
helpviewer_keywords:
- GetILFunctionBodyAllocator method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBodyAllocator method [.NET Framework profiling]
ms.assetid: 5da1bf3d-dddf-4892-b266-578ee54d570b
topic_type:
- apiref
ms.openlocfilehash: 967f38add9ae5996c6ac33388203b55161a84e39
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498267"
---
# <a name="icorprofilerinfogetilfunctionbodyallocator-method"></a>ICorProfilerInfo::GetILFunctionBodyAllocator 方法
取得介面，它會提供方法來配置記憶體，以用於交換 Microsoft 中繼語言（MSIL）程式碼中方法的主體。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetILFunctionBodyAllocator(  
    [in]  ModuleID      moduleId,  
    [out] IMethodMalloc **ppMalloc);  
```  
  
## <a name="parameters"></a>參數  
 `moduleId`  
 在方法所在模組的識別碼。  
  
 `ppMalloc`  
 脫銷提供方法來配置記憶體的[IMethodMalloc](imethodmalloc-interface.md)介面指標。  
  
## <a name="remarks"></a>備註  
 MSIL 程式碼中的方法主體必須位於相對於已載入模組的相對虛擬位址（RVA），這表示它會遵循 4 GB 內的模組。 為了讓工具能夠更輕鬆地交換方法的主體， `GetILFunctionBodyAllocator` 方法可確保記憶體會在該範圍內配置。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
