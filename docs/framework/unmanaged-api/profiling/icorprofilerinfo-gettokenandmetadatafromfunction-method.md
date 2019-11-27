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
ms.openlocfilehash: b3e14230888e9bf846879d5728c2b20883fb8d53
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438735"
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a><span data-ttu-id="ac32f-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction 方法</span><span class="sxs-lookup"><span data-stu-id="ac32f-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Method</span></span>
<span data-ttu-id="ac32f-103">取得元資料標記，以及可用於指定函式之標記的中繼資料介面實例。</span><span class="sxs-lookup"><span data-stu-id="ac32f-103">Gets the metadata token and a metadata interface instance that can be used against the token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac32f-104">語法</span><span class="sxs-lookup"><span data-stu-id="ac32f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac32f-105">參數</span><span class="sxs-lookup"><span data-stu-id="ac32f-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="ac32f-106">在要取得元資料標記和中繼資料介面的函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="ac32f-106">[in] The ID of the function for which to get the metadata token and metadata interface.</span></span>  
  
 `riid`  
 <span data-ttu-id="ac32f-107">在要取得實例之中繼資料介面的參考識別碼。</span><span class="sxs-lookup"><span data-stu-id="ac32f-107">[in] The reference ID of the metadata interface to get the instance of.</span></span>  
  
 `ppImport`  
 <span data-ttu-id="ac32f-108">脫銷中繼資料介面實例位址的指標，可用於所指定函式的 token。</span><span class="sxs-lookup"><span data-stu-id="ac32f-108">[out] A pointer to the address of the metadata interface instance that can be used against the token for the specified function.</span></span>  
  
 `pToken`  
 <span data-ttu-id="ac32f-109">脫銷所指定函式之元資料標記的指標。</span><span class="sxs-lookup"><span data-stu-id="ac32f-109">[out] A pointer to the metadata token for the specified function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac32f-110">需求</span><span class="sxs-lookup"><span data-stu-id="ac32f-110">Requirements</span></span>  
 <span data-ttu-id="ac32f-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ac32f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac32f-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ac32f-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ac32f-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac32f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac32f-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac32f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac32f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac32f-115">See also</span></span>

- [<span data-ttu-id="ac32f-116">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="ac32f-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
