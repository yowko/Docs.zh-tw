---
title: ICorProfilerInfo::GetClassIDInfo 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassIDInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassIDInfo
helpviewer_keywords:
- GetClassIDInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetClassIDInfo method [.NET Framework profiling]
ms.assetid: 9e93b99e-5aca-415c-8e37-7f33753b612d
topic_type:
- apiref
ms.openlocfilehash: 4fbee938ae86b338f2beb0b48feeee46f144a4a0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498488"
---
# <a name="icorprofilerinfogetclassidinfo-method"></a>ICorProfilerInfo::GetClassIDInfo 方法
取得指定類別的父模組和元資料標記。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetClassIDInfo(  
    [in]  ClassID   classId,  
    [out] ModuleID  *pModuleId,  
    [out] mdTypeDef *pTypeDefToken);  
```  
  
## <a name="parameters"></a>參數  
 `classId`  
 在要取得其資訊之類別的識別碼。  
  
 `pModuleId`  
 脫銷類別之父模組的識別碼指標。  
  
 `pTypeDefToken`  
 脫銷類別之元資料標記的指標。  
  
## <a name="remarks"></a>備註  
 分析工具程式碼可以呼叫[ICorProfilerInfo：： GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md)來取得給定模組的中繼資料介面。 然後，傳回至 `pTypeDefToken` 所參考位置的中繼資料語彙基元可以用來存取此類別的中繼資料。  
  
 若要取得泛型型別的詳細資訊，請使用[ICorProfilerInfo2：： GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md)。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
