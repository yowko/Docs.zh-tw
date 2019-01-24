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
ms.openlocfilehash: 89475ebc5ef04c8693adb7a83bd1dd07f5774fb9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54544688"
---
# <a name="imetadataemitsetrva-method"></a><span data-ttu-id="b8a6f-102">IMetaDataEmit::SetRVA 方法</span><span class="sxs-lookup"><span data-stu-id="b8a6f-102">IMetaDataEmit::SetRVA Method</span></span>
<span data-ttu-id="b8a6f-103">設定指定之方法的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="b8a6f-103">Sets the relative virtual address of the specified method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8a6f-104">語法</span><span class="sxs-lookup"><span data-stu-id="b8a6f-104">Syntax</span></span>  
  
```  
HRESULT SetRVA (  
    [in]  mdMethodDef  md,   
    [in]  ULONG        ulRVA   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b8a6f-105">參數</span><span class="sxs-lookup"><span data-stu-id="b8a6f-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="b8a6f-106">[in]目標方法或方法的實作之語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b8a6f-106">[in] The token for the target method or method implementation.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="b8a6f-107">[in]程式碼或資料區域的位址。</span><span class="sxs-lookup"><span data-stu-id="b8a6f-107">[in] The address of the code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8a6f-108">需求</span><span class="sxs-lookup"><span data-stu-id="b8a6f-108">Requirements</span></span>  
 <span data-ttu-id="b8a6f-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b8a6f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8a6f-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b8a6f-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b8a6f-111">**程式庫：** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b8a6f-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b8a6f-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8a6f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8a6f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8a6f-113">See also</span></span>
- [<span data-ttu-id="b8a6f-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="b8a6f-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b8a6f-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="b8a6f-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
