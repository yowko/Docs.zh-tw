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
ms.openlocfilehash: 8e03eefc3758347389be4af6d53921480ee40263
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724074"
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a><span data-ttu-id="2f042-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction 方法</span><span class="sxs-lookup"><span data-stu-id="2f042-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Method</span></span>

<span data-ttu-id="2f042-103">取得中繼資料 token 和中繼資料介面實例，可針對指定之函式的 token 使用。</span><span class="sxs-lookup"><span data-stu-id="2f042-103">Gets the metadata token and a metadata interface instance that can be used against the token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f042-104">語法</span><span class="sxs-lookup"><span data-stu-id="2f042-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f042-105">參數</span><span class="sxs-lookup"><span data-stu-id="2f042-105">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="2f042-106">在取得元資料標記和中繼資料介面的函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="2f042-106">[in] The ID of the function for which to get the metadata token and metadata interface.</span></span>  
  
 `riid`  
 <span data-ttu-id="2f042-107">在要取得其實例之中繼資料介面的參考識別碼。</span><span class="sxs-lookup"><span data-stu-id="2f042-107">[in] The reference ID of the metadata interface to get the instance of.</span></span>  
  
 `ppImport`  
 <span data-ttu-id="2f042-108">擴展中繼資料介面實例位址的指標，可針對指定之函式的 token 使用。</span><span class="sxs-lookup"><span data-stu-id="2f042-108">[out] A pointer to the address of the metadata interface instance that can be used against the token for the specified function.</span></span>  
  
 `pToken`  
 <span data-ttu-id="2f042-109">擴展指定之函數的元資料標記指標。</span><span class="sxs-lookup"><span data-stu-id="2f042-109">[out] A pointer to the metadata token for the specified function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f042-110">需求</span><span class="sxs-lookup"><span data-stu-id="2f042-110">Requirements</span></span>  

 <span data-ttu-id="2f042-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2f042-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f042-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2f042-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2f042-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f042-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f042-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f042-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f042-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f042-115">See also</span></span>

- [<span data-ttu-id="2f042-116">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="2f042-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
