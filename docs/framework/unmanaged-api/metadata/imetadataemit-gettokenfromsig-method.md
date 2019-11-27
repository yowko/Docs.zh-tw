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
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="f82b3-102">IMetaDataEmit::GetTokenFromSig 方法</span><span class="sxs-lookup"><span data-stu-id="f82b3-102">IMetaDataEmit::GetTokenFromSig Method</span></span>
<span data-ttu-id="f82b3-103">取得指定之中繼資料簽章的 token。</span><span class="sxs-lookup"><span data-stu-id="f82b3-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f82b3-104">語法</span><span class="sxs-lookup"><span data-stu-id="f82b3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromSig (   
    [in]  PCCOR_SIGNATURE pvSig,   
    [in]  ULONG       cbSig,   
    [out] mdSignature *pmsig   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f82b3-105">參數</span><span class="sxs-lookup"><span data-stu-id="f82b3-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="f82b3-106">在要保存並儲存的簽章。</span><span class="sxs-lookup"><span data-stu-id="f82b3-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="f82b3-107">在`pvSig`中的位元組計數。</span><span class="sxs-lookup"><span data-stu-id="f82b3-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="f82b3-108">脫銷指派的 `mdSignature` token。</span><span class="sxs-lookup"><span data-stu-id="f82b3-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f82b3-109">需求</span><span class="sxs-lookup"><span data-stu-id="f82b3-109">Requirements</span></span>  
 <span data-ttu-id="f82b3-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f82b3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f82b3-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="f82b3-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f82b3-112">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="f82b3-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f82b3-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f82b3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f82b3-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="f82b3-114">See also</span></span>

- [<span data-ttu-id="f82b3-115">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="f82b3-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f82b3-116">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="f82b3-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
