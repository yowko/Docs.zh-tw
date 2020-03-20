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
ms.openlocfilehash: d02943f28435fc00aad8e319aa260a24cca5e307
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177594"
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="3038e-102">IMetaDataEmit::GetTokenFromSig 方法</span><span class="sxs-lookup"><span data-stu-id="3038e-102">IMetaDataEmit::GetTokenFromSig Method</span></span>
<span data-ttu-id="3038e-103">獲取指定中繼資料簽名的權杖。</span><span class="sxs-lookup"><span data-stu-id="3038e-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3038e-104">語法</span><span class="sxs-lookup"><span data-stu-id="3038e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromSig (
    [in]  PCCOR_SIGNATURE pvSig,
    [in]  ULONG       cbSig,
    [out] mdSignature *pmsig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3038e-105">參數</span><span class="sxs-lookup"><span data-stu-id="3038e-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="3038e-106">[在]要保留和存儲的簽名。</span><span class="sxs-lookup"><span data-stu-id="3038e-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="3038e-107">[在]中的`pvSig`位元組計數。</span><span class="sxs-lookup"><span data-stu-id="3038e-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="3038e-108">[出]分配的`mdSignature`權杖。</span><span class="sxs-lookup"><span data-stu-id="3038e-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3038e-109">需求</span><span class="sxs-lookup"><span data-stu-id="3038e-109">Requirements</span></span>  
 <span data-ttu-id="3038e-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3038e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3038e-111">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="3038e-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3038e-112">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3038e-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3038e-113">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3038e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3038e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3038e-114">See also</span></span>

- [<span data-ttu-id="3038e-115">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="3038e-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="3038e-116">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="3038e-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
