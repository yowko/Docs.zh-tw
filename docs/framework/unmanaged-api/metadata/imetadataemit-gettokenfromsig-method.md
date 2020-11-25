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
ms.openlocfilehash: b41891227d94b66bf59128d620eba9da117fe92a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722045"
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="2d472-102">IMetaDataEmit::GetTokenFromSig 方法</span><span class="sxs-lookup"><span data-stu-id="2d472-102">IMetaDataEmit::GetTokenFromSig Method</span></span>

<span data-ttu-id="2d472-103">取得指定之中繼資料簽章的標記。</span><span class="sxs-lookup"><span data-stu-id="2d472-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d472-104">語法</span><span class="sxs-lookup"><span data-stu-id="2d472-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromSig (
    [in]  PCCOR_SIGNATURE pvSig,
    [in]  ULONG       cbSig,
    [out] mdSignature *pmsig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d472-105">參數</span><span class="sxs-lookup"><span data-stu-id="2d472-105">Parameters</span></span>  

 `pvSig`  
 <span data-ttu-id="2d472-106">在要保存和儲存的簽章。</span><span class="sxs-lookup"><span data-stu-id="2d472-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="2d472-107">在中的位元組計數 `pvSig` 。</span><span class="sxs-lookup"><span data-stu-id="2d472-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="2d472-108">擴展 `mdSignature` 指派的權杖。</span><span class="sxs-lookup"><span data-stu-id="2d472-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d472-109">需求</span><span class="sxs-lookup"><span data-stu-id="2d472-109">Requirements</span></span>  

 <span data-ttu-id="2d472-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2d472-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d472-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="2d472-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2d472-112">連結 **庫：** 當做 MSCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="2d472-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2d472-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d472-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d472-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d472-114">See also</span></span>

- [<span data-ttu-id="2d472-115">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="2d472-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="2d472-116">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="2d472-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
