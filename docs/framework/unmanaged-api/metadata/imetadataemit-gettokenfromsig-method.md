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
ms.openlocfilehash: f1262181fa745e1b6d3fc48a4ad728c1020705b5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434323"
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="2d723-102">IMetaDataEmit::GetTokenFromSig 方法</span><span class="sxs-lookup"><span data-stu-id="2d723-102">IMetaDataEmit::GetTokenFromSig Method</span></span>
<span data-ttu-id="2d723-103">Gets a token for the specified metadata signature.</span><span class="sxs-lookup"><span data-stu-id="2d723-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d723-104">語法</span><span class="sxs-lookup"><span data-stu-id="2d723-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromSig (   
    [in]  PCCOR_SIGNATURE pvSig,   
    [in]  ULONG       cbSig,   
    [out] mdSignature *pmsig   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d723-105">參數</span><span class="sxs-lookup"><span data-stu-id="2d723-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="2d723-106">[in] The signature to be persisted and stored.</span><span class="sxs-lookup"><span data-stu-id="2d723-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="2d723-107">[in] The count of bytes in `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="2d723-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="2d723-108">[out] The `mdSignature` token assigned.</span><span class="sxs-lookup"><span data-stu-id="2d723-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d723-109">需求</span><span class="sxs-lookup"><span data-stu-id="2d723-109">Requirements</span></span>  
 <span data-ttu-id="2d723-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2d723-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d723-111">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2d723-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2d723-112">**Library:** Used as a resource in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2d723-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2d723-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d723-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d723-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="2d723-114">See also</span></span>

- [<span data-ttu-id="2d723-115">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="2d723-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="2d723-116">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="2d723-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
