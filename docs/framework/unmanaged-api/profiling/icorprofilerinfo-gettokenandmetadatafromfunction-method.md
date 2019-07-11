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
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a><span data-ttu-id="57338-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction 方法</span><span class="sxs-lookup"><span data-stu-id="57338-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Method</span></span>
<span data-ttu-id="57338-103">取得中繼資料語彙基元和中繼資料介面執行個體可以使用語彙基元，為指定的函式。</span><span class="sxs-lookup"><span data-stu-id="57338-103">Gets the metadata token and a metadata interface instance that can be used against the token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57338-104">語法</span><span class="sxs-lookup"><span data-stu-id="57338-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57338-105">參數</span><span class="sxs-lookup"><span data-stu-id="57338-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="57338-106">[in]要取得的中繼資料語彙基元和中繼資料介面函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="57338-106">[in] The ID of the function for which to get the metadata token and metadata interface.</span></span>  
  
 `riid`  
 <span data-ttu-id="57338-107">[in]要取得的執行個體中繼資料介面的參考識別碼。</span><span class="sxs-lookup"><span data-stu-id="57338-107">[in] The reference ID of the metadata interface to get the instance of.</span></span>  
  
 `ppImport`  
 <span data-ttu-id="57338-108">[out]中繼資料介面執行個體可以使用語彙基元，為指定的函式的位址指標。</span><span class="sxs-lookup"><span data-stu-id="57338-108">[out] A pointer to the address of the metadata interface instance that can be used against the token for the specified function.</span></span>  
  
 `pToken`  
 <span data-ttu-id="57338-109">[out]指定的函式的中繼資料語彙基元指標。</span><span class="sxs-lookup"><span data-stu-id="57338-109">[out] A pointer to the metadata token for the specified function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57338-110">需求</span><span class="sxs-lookup"><span data-stu-id="57338-110">Requirements</span></span>  
 <span data-ttu-id="57338-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="57338-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57338-112">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="57338-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="57338-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57338-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57338-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57338-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57338-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57338-115">See also</span></span>

- [<span data-ttu-id="57338-116">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="57338-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
