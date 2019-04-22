---
title: IMetaDataEmit::GetTokenFromSig 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetTokenFromSig
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetTokenFromSig
helpviewer_keywords:
- IMetaDataEmit::GetTokenFromSig method [.NET Framework metadata]
- GetTokenFromSig method [.NET Framework metadata]
ms.assetid: 50a58a83-6287-40a4-b315-47823cea0a5c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 242618fb2a5ab748132baf68e24240d1ffaf2301
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59139837"
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="7cf11-102">IMetaDataEmit::GetTokenFromSig 方法</span><span class="sxs-lookup"><span data-stu-id="7cf11-102">IMetaDataEmit::GetTokenFromSig Method</span></span>
<span data-ttu-id="7cf11-103">取得指定之中繼資料簽章的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="7cf11-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cf11-104">語法</span><span class="sxs-lookup"><span data-stu-id="7cf11-104">Syntax</span></span>  
  
```  
HRESULT GetTokenFromSig (   
    [in]  PCCOR_SIGNATURE pvSig,   
    [in]  ULONG       cbSig,   
    [out] mdSignature *pmsig   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7cf11-105">參數</span><span class="sxs-lookup"><span data-stu-id="7cf11-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="7cf11-106">[in]要保存及儲存的簽章。</span><span class="sxs-lookup"><span data-stu-id="7cf11-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="7cf11-107">[in]中的位元組計數`pvSig`。</span><span class="sxs-lookup"><span data-stu-id="7cf11-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="7cf11-108">[out]`mdSignature`指派權杖。</span><span class="sxs-lookup"><span data-stu-id="7cf11-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cf11-109">需求</span><span class="sxs-lookup"><span data-stu-id="7cf11-109">Requirements</span></span>  
 <span data-ttu-id="7cf11-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7cf11-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cf11-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7cf11-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7cf11-112">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7cf11-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7cf11-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cf11-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cf11-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7cf11-114">See also</span></span>

- [<span data-ttu-id="7cf11-115">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="7cf11-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="7cf11-116">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="7cf11-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
