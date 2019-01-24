---
title: ICorProfilerInfo2::GetClassFromTokenAndTypeArgs 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs
helpviewer_keywords:
- GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: b25c88f0-71b9-443b-8eea-1c94db0a44b9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0651609e6d2597336ee42ceae752df7e561cd252
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692648"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetClassFromTokenAndTypeArgs 方法
取得`ClassID`使用指定的中繼資料語彙基元型別和`ClassID`值的任何型別引數。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
#### <a name="parameters"></a>參數  
 `moduleID`  
 [in]型別所在之模組識別碼。  
  
 `typeDef`  
 [in]`mdTypeDef`參考類型的中繼資料語彙基元。  
  
 `cTypeArgs`  
 [in]指定型別的型別參數的數目。 此值必須是非泛型型別為零。  
  
 `typeArgs`  
 [in]陣列`ClassID`每一個都是類型的引數的值。 值`typeArgs`可以是 NULL，如果`cTypeArgs`設為零。  
  
 `pClassID`  
 [out]指標`ClassID`指定的型別。  
  
## <a name="remarks"></a>備註  
 呼叫`GetClassFromTokenAndTypeArgs`方法`mdTypeRef`而不是`mdTypeDef`中繼資料語彙基元可能會有無法預期的結果，呼叫端應該解決`mdTypeRef`到`mdTypeDef`傳遞時。  
  
 如果尚未載入的型別，則呼叫`GetClassFromTokenAndTypeArgs`會觸發載入，而這是危險的作業在許多內容中。 例如，在載入模組或其他類型期間呼叫這個方法可能會導致無限迴圈循環載入嘗試執行階段。  
  
 一般情況下，使用`GetClassFromTokenAndTypeArgs`建議您不要使用。 如果分析工具想要針對特定類型的事件，它們應該儲存`ModuleID`並`mdTypeDef`該類型，以及使用[ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)來檢查是否指定`ClassID`，就是所需的類型。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
