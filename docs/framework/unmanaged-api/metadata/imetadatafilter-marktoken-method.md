---
title: IMetaDataFilter::MarkToken 方法
ms.date: 03/30/2017
api_name:
- IMetaDataFilter.MarkToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter::MarkToken
helpviewer_keywords:
- IMetaDataFilter::MarkToken method [.NET Framework metadata]
- MarkToken method, IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: bd492834-6529-4d39-b93d-f8cdbd3e297f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6fdd50f0de014aa68b14303e9e22924b0790fa55
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786265"
---
# <a name="imetadatafiltermarktoken-method"></a><span data-ttu-id="dea5a-102">IMetaDataFilter::MarkToken 方法</span><span class="sxs-lookup"><span data-stu-id="dea5a-102">IMetaDataFilter::MarkToken Method</span></span>
<span data-ttu-id="dea5a-103">設定值，指出指定的中繼資料語彙基元已處理。</span><span class="sxs-lookup"><span data-stu-id="dea5a-103">Sets a value indicating that the specified metadata token has been processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dea5a-104">語法</span><span class="sxs-lookup"><span data-stu-id="dea5a-104">Syntax</span></span>  
  
```  
HRESULT MarkToken (  
    [in] mdToken   tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dea5a-105">參數</span><span class="sxs-lookup"><span data-stu-id="dea5a-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="dea5a-106">[in]要標記為已處理的權杖。</span><span class="sxs-lookup"><span data-stu-id="dea5a-106">[in] The token to mark as processed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dea5a-107">需求</span><span class="sxs-lookup"><span data-stu-id="dea5a-107">Requirements</span></span>  
 <span data-ttu-id="dea5a-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dea5a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dea5a-109">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dea5a-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dea5a-110">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="dea5a-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dea5a-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dea5a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dea5a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dea5a-112">See also</span></span>

- [<span data-ttu-id="dea5a-113">IMetaDataFilter 介面</span><span class="sxs-lookup"><span data-stu-id="dea5a-113">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
