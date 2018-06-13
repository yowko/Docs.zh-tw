---
title: IMetaDataEmit::SetRVA 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetRVA
helpviewer_keywords:
- IMetaDataEmit::SetRVA method [.NET Framework metadata]
- SetRVA method [.NET Framework metadata]
ms.assetid: 4d69fb6d-ee35-4318-8224-5eea2bd16818
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 371eed84883e2816892c0a6a212a4a89a287cc58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445269"
---
# <a name="imetadataemitsetrva-method"></a><span data-ttu-id="bc563-102">IMetaDataEmit::SetRVA 方法</span><span class="sxs-lookup"><span data-stu-id="bc563-102">IMetaDataEmit::SetRVA Method</span></span>
<span data-ttu-id="bc563-103">設定指定之方法的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="bc563-103">Sets the relative virtual address of the specified method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc563-104">語法</span><span class="sxs-lookup"><span data-stu-id="bc563-104">Syntax</span></span>  
  
```  
HRESULT SetRVA (  
    [in]  mdMethodDef  md,   
    [in]  ULONG        ulRVA   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bc563-105">參數</span><span class="sxs-lookup"><span data-stu-id="bc563-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="bc563-106">[in]目標方法或方法實作語彙基元。</span><span class="sxs-lookup"><span data-stu-id="bc563-106">[in] The token for the target method or method implementation.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="bc563-107">[in]程式碼或資料區的位址。</span><span class="sxs-lookup"><span data-stu-id="bc563-107">[in] The address of the code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc563-108">需求</span><span class="sxs-lookup"><span data-stu-id="bc563-108">Requirements</span></span>  
 <span data-ttu-id="bc563-109">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bc563-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc563-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bc563-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bc563-111">**程式庫：** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="bc563-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bc563-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc563-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc563-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc563-113">See Also</span></span>  
 [<span data-ttu-id="bc563-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="bc563-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="bc563-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="bc563-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
