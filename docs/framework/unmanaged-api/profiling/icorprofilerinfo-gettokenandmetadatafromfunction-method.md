---
title: "ICorProfilerInfo::GetTokenAndMetadataFromFunction 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetTokenAndMetadataFromFunction
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetTokenAndMetadataFromFunction
helpviewer_keywords:
- ICorProfilerInfo::GetTokenAndMetadataFromFunction method [.NET Framework profiling]
- GetTokenAndMetadataFromFunction method [.NET Framework profiling]
ms.assetid: e525aa16-c923-4b16-833b-36f1f0dd70fc
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 585b28161814045777cf2294f78bafc3229bfae9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a><span data-ttu-id="e8cf2-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction 方法</span><span class="sxs-lookup"><span data-stu-id="e8cf2-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Method</span></span>
<span data-ttu-id="e8cf2-103">取得中繼資料語彙基元和可用於語彙基元的指定函式的中繼資料介面執行個體。</span><span class="sxs-lookup"><span data-stu-id="e8cf2-103">Gets the metadata token and a metadata interface instance that can be used against the token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8cf2-104">語法</span><span class="sxs-lookup"><span data-stu-id="e8cf2-104">Syntax</span></span>  
  
```  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e8cf2-105">參數</span><span class="sxs-lookup"><span data-stu-id="e8cf2-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="e8cf2-106">[in]用來取得中繼資料語彙基元和中繼資料介面的函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="e8cf2-106">[in] The ID of the function for which to get the metadata token and metadata interface.</span></span>  
  
 `riid`  
 <span data-ttu-id="e8cf2-107">[in]要取得的執行個體的中繼資料介面的參考識別碼。</span><span class="sxs-lookup"><span data-stu-id="e8cf2-107">[in] The reference ID of the metadata interface to get the instance of.</span></span>  
  
 `ppImport`  
 <span data-ttu-id="e8cf2-108">[out]可以使用語彙基元，指定函式的中繼資料介面執行個體的位址指標。</span><span class="sxs-lookup"><span data-stu-id="e8cf2-108">[out] A pointer to the address of the metadata interface instance that can be used against the token for the specified function.</span></span>  
  
 `pToken`  
 <span data-ttu-id="e8cf2-109">[out]指定的函式的中繼資料語彙基元指標。</span><span class="sxs-lookup"><span data-stu-id="e8cf2-109">[out] A pointer to the metadata token for the specified function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8cf2-110">需求</span><span class="sxs-lookup"><span data-stu-id="e8cf2-110">Requirements</span></span>  
 <span data-ttu-id="e8cf2-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e8cf2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8cf2-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e8cf2-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e8cf2-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8cf2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8cf2-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8cf2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8cf2-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8cf2-115">See Also</span></span>  
 [<span data-ttu-id="e8cf2-116">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="e8cf2-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
