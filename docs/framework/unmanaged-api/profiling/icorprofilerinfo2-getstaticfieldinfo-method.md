---
title: ICorProfilerInfo2::GetStaticFieldInfo 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStaticFieldInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo method [.NET Framework profiling]
- GetStaticFieldInfo method [.NET Framework profiling]
ms.assetid: fc663e76-e23f-49a8-bdd5-52cdf1a3b2b3
topic_type:
- apiref
ms.openlocfilehash: ff84bdfb8bbd5331fb94eed766f09137adf9e62c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703833"
---
# <a name="icorprofilerinfo2getstaticfieldinfo-method"></a>ICorProfilerInfo2::GetStaticFieldInfo 方法

取得值，這個值表示套用至指定之欄位的靜態類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetStaticFieldInfo (  
    [in] ClassID               classId,  
    [in] mdFieldDef            fieldToken,  
    [out] COR_PRF_STATIC_TYPE  *pFieldInfo);  
```  
  
## <a name="parameters"></a>參數  

 `classId`  
 在定義靜態欄位之類別的識別碼。  
  
 `fieldToken`  
 在靜態欄位的元資料標記。  
  
 `pFieldInfo`  
 擴展 [COR_PRF_STATIC_TYPE](cor-prf-static-type-enumeration.md) 列舉值的指標，指出指定的欄位是否為靜態，如果是，則為套用至欄位的靜態類型。  
  
## <a name="remarks"></a>備註  

 這項資訊可以用來判斷要呼叫哪一個函式，以取得靜態欄位的位址。  
  
 分析工具程式碼仍應檢查靜態欄位的中繼資料，以確保其確實具有位址。 靜態常值 (也就是說，常數) 只存在於中繼資料中，且沒有位址。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 介面](icorprofilerinfo2-interface.md)
