---
title: ICorProfilerInfo::GetTokenAndMetadataFromFunction 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetTokenAndMetadataFromFunction
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetTokenAndMetadataFromFunction
helpviewer_keywords:
- ICorProfilerInfo::GetTokenAndMetadataFromFunction method [.NET Framework profiling]
- GetTokenAndMetadataFromFunction method [.NET Framework profiling]
ms.assetid: e525aa16-c923-4b16-833b-36f1f0dd70fc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b608b8818890bdb27a956a90c7987cf7c421304d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772265"
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a>ICorProfilerInfo::GetTokenAndMetadataFromFunction 方法
取得中繼資料語彙基元和中繼資料介面執行個體可以使用語彙基元，為指定的函式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a>參數  
 `functionId`  
 [in]要取得的中繼資料語彙基元和中繼資料介面函式的識別碼。  
  
 `riid`  
 [in]要取得的執行個體中繼資料介面的參考識別碼。  
  
 `ppImport`  
 [out]中繼資料介面執行個體可以使用語彙基元，為指定的函式的位址指標。  
  
 `pToken`  
 [out]指定的函式的中繼資料語彙基元指標。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
