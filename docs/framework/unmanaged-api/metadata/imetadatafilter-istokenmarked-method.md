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
ms.openlocfilehash: 5bf5149e8e42a810a6a490767638b374f66b5679
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445860"
---
# <a name="imetadatafilteristokenmarked-method"></a><span data-ttu-id="9c3f6-102">IMetaDataFilter::IsTokenMarked 方法</span><span class="sxs-lookup"><span data-stu-id="9c3f6-102">IMetaDataFilter::IsTokenMarked Method</span></span>
<span data-ttu-id="9c3f6-103">取得值，指出指定的中繼資料語彙基元是否已標示為處理。</span><span class="sxs-lookup"><span data-stu-id="9c3f6-103">Gets a value indicating whether the specified metadata token has been marked as processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c3f6-104">語法</span><span class="sxs-lookup"><span data-stu-id="9c3f6-104">Syntax</span></span>  
  
```  
HRESULT IsTokenMarked (  
    [in]  mdToken  tk,   
    [out] BOOL     *pIsMarked  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9c3f6-105">參數</span><span class="sxs-lookup"><span data-stu-id="9c3f6-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="9c3f6-106">[in]要檢查處理標記的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="9c3f6-106">[in] The token to examine for a processing mark.</span></span>  
  
 `pIsMarked`  
 <span data-ttu-id="9c3f6-107">[out]值是`true`如果`tk`已處理，否則為`false`。</span><span class="sxs-lookup"><span data-stu-id="9c3f6-107">[out] A value that is `true` if `tk` has been processed; otherwise `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c3f6-108">需求</span><span class="sxs-lookup"><span data-stu-id="9c3f6-108">Requirements</span></span>  
 <span data-ttu-id="9c3f6-109">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9c3f6-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c3f6-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9c3f6-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9c3f6-111">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9c3f6-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9c3f6-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c3f6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c3f6-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c3f6-113">See Also</span></span>  
 [<span data-ttu-id="9c3f6-114">IMetaDataFilter 介面</span><span class="sxs-lookup"><span data-stu-id="9c3f6-114">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
