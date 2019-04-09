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
ms.openlocfilehash: e17a6846ba0276ec7ba423ab25e3f11baf278d03
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098750"
---
# <a name="imetadataemitsetrva-method"></a><span data-ttu-id="fa0c1-102">IMetaDataEmit::SetRVA 方法</span><span class="sxs-lookup"><span data-stu-id="fa0c1-102">IMetaDataEmit::SetRVA Method</span></span>
<span data-ttu-id="fa0c1-103">設定指定之方法的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="fa0c1-103">Sets the relative virtual address of the specified method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa0c1-104">語法</span><span class="sxs-lookup"><span data-stu-id="fa0c1-104">Syntax</span></span>  
  
```  
HRESULT SetRVA (  
    [in]  mdMethodDef  md,   
    [in]  ULONG        ulRVA   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa0c1-105">參數</span><span class="sxs-lookup"><span data-stu-id="fa0c1-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="fa0c1-106">[in]目標方法或方法的實作之語彙基元。</span><span class="sxs-lookup"><span data-stu-id="fa0c1-106">[in] The token for the target method or method implementation.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="fa0c1-107">[in]程式碼或資料區域的位址。</span><span class="sxs-lookup"><span data-stu-id="fa0c1-107">[in] The address of the code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa0c1-108">需求</span><span class="sxs-lookup"><span data-stu-id="fa0c1-108">Requirements</span></span>  
 <span data-ttu-id="fa0c1-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fa0c1-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa0c1-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fa0c1-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fa0c1-111">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="fa0c1-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="fa0c1-112">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="fa0c1-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fa0c1-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa0c1-113">See also</span></span>

- [<span data-ttu-id="fa0c1-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="fa0c1-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="fa0c1-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="fa0c1-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
