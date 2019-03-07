---
title: IMetaDataEmit::SaveToStream 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToStream
helpviewer_keywords:
- IMetaDataEmit::SaveToStream method [.NET Framework metadata]
- SaveToStream method [.NET Framework metadata]
ms.assetid: e0290a49-3818-4a43-ad46-3014faa34f97
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d2b7f0925946435bd69596f47e956f1f96eec7b2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502926"
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="6fe5c-102">IMetaDataEmit::SaveToStream 方法</span><span class="sxs-lookup"><span data-stu-id="6fe5c-102">IMetaDataEmit::SaveToStream Method</span></span>
<span data-ttu-id="6fe5c-103">將所有的中繼資料儲存至指定目前範圍中`IStream`。</span><span class="sxs-lookup"><span data-stu-id="6fe5c-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fe5c-104">語法</span><span class="sxs-lookup"><span data-stu-id="6fe5c-104">Syntax</span></span>  
  
```  
HRESULT SaveToStream (   
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6fe5c-105">參數</span><span class="sxs-lookup"><span data-stu-id="6fe5c-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="6fe5c-106">[in]若要將儲存到可寫入的資料流。</span><span class="sxs-lookup"><span data-stu-id="6fe5c-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="6fe5c-107">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="6fe5c-107">[in] Reserved.</span></span> <span data-ttu-id="6fe5c-108">必須是零。</span><span class="sxs-lookup"><span data-stu-id="6fe5c-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fe5c-109">需求</span><span class="sxs-lookup"><span data-stu-id="6fe5c-109">Requirements</span></span>  
 <span data-ttu-id="6fe5c-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6fe5c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fe5c-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6fe5c-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6fe5c-112">**程式庫：** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6fe5c-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6fe5c-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fe5c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fe5c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6fe5c-114">See also</span></span>
- [<span data-ttu-id="6fe5c-115">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="6fe5c-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="6fe5c-116">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="6fe5c-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
