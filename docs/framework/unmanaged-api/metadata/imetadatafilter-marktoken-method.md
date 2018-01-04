---
title: "IMetaDataFilter::MarkToken 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataFilter.MarkToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataFilter::MarkToken
helpviewer_keywords:
- IMetaDataFilter::MarkToken method [.NET Framework metadata]
- MarkToken method, IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: bd492834-6529-4d39-b93d-f8cdbd3e297f
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fb40d7674caae119b39f49b0c1024c7500bc892a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatafiltermarktoken-method"></a><span data-ttu-id="57498-102">IMetaDataFilter::MarkToken 方法</span><span class="sxs-lookup"><span data-stu-id="57498-102">IMetaDataFilter::MarkToken Method</span></span>
<span data-ttu-id="57498-103">設定值，指出指定的中繼資料語彙基元已經處理。</span><span class="sxs-lookup"><span data-stu-id="57498-103">Sets a value indicating that the specified metadata token has been processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57498-104">語法</span><span class="sxs-lookup"><span data-stu-id="57498-104">Syntax</span></span>  
  
```  
HRESULT MarkToken (  
    [in] mdToken   tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="57498-105">參數</span><span class="sxs-lookup"><span data-stu-id="57498-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="57498-106">[in]要標記為已處理的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="57498-106">[in] The token to mark as processed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57498-107">需求</span><span class="sxs-lookup"><span data-stu-id="57498-107">Requirements</span></span>  
 <span data-ttu-id="57498-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="57498-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57498-109">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="57498-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="57498-110">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="57498-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="57498-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57498-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57498-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="57498-112">See Also</span></span>  
 [<span data-ttu-id="57498-113">IMetaDataFilter 介面</span><span class="sxs-lookup"><span data-stu-id="57498-113">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
