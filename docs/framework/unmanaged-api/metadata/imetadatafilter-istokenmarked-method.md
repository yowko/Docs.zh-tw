---
title: IMetaDataFilter::IsTokenMarked 方法
ms.date: 03/30/2017
api_name:
- IMetaDataFilter.IsTokenMarked
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter::IsTokenMarked
helpviewer_keywords:
- IMetaDataFilter::IsTokenMarked method [.NET Framework metadata]
- IsTokenMarked method [.NET Framework metadata]
ms.assetid: 7d90dcee-0206-4540-807b-06982fe65f1a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e15f4e8691db13b9a646a1e1d783075acfcdd896
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777075"
---
# <a name="imetadatafilteristokenmarked-method"></a><span data-ttu-id="da09d-102">IMetaDataFilter::IsTokenMarked 方法</span><span class="sxs-lookup"><span data-stu-id="da09d-102">IMetaDataFilter::IsTokenMarked Method</span></span>
<span data-ttu-id="da09d-103">取得值，指出指定的中繼資料語彙基元是否已標示為已處理。</span><span class="sxs-lookup"><span data-stu-id="da09d-103">Gets a value indicating whether the specified metadata token has been marked as processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da09d-104">語法</span><span class="sxs-lookup"><span data-stu-id="da09d-104">Syntax</span></span>  
  
```cpp  
HRESULT IsTokenMarked (  
    [in]  mdToken  tk,   
    [out] BOOL     *pIsMarked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da09d-105">參數</span><span class="sxs-lookup"><span data-stu-id="da09d-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="da09d-106">[in]要檢查處理標記的權杖。</span><span class="sxs-lookup"><span data-stu-id="da09d-106">[in] The token to examine for a processing mark.</span></span>  
  
 `pIsMarked`  
 <span data-ttu-id="da09d-107">[out]值是`true`如果`tk`已經過處理，否則為`false`。</span><span class="sxs-lookup"><span data-stu-id="da09d-107">[out] A value that is `true` if `tk` has been processed; otherwise `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da09d-108">需求</span><span class="sxs-lookup"><span data-stu-id="da09d-108">Requirements</span></span>  
 <span data-ttu-id="da09d-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="da09d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da09d-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="da09d-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="da09d-111">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="da09d-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="da09d-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da09d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da09d-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da09d-113">See also</span></span>

- [<span data-ttu-id="da09d-114">IMetaDataFilter 介面</span><span class="sxs-lookup"><span data-stu-id="da09d-114">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
