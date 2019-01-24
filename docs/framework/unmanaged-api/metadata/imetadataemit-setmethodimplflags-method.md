---
title: IMetaDataEmit::SetMethodImplFlags 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodImplFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodImplFlags
helpviewer_keywords:
- IMetaDataEmit::SetMethodImplFlags method [.NET Framework metadata]
- SetMethodImpFlags method [.NET Framework metadata]
ms.assetid: 4bc82d9b-9544-4be3-ba51-a2d4d806158a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cffbf01cb8098f30fb026491e0153ac9a651756a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692386"
---
# <a name="imetadataemitsetmethodimplflags-method"></a><span data-ttu-id="06d81-102">IMetaDataEmit::SetMethodImplFlags 方法</span><span class="sxs-lookup"><span data-stu-id="06d81-102">IMetaDataEmit::SetMethodImplFlags Method</span></span>
<span data-ttu-id="06d81-103">設定或更新繼承的方法實作所指定的語彙基元所參考的中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="06d81-103">Sets or updates the metadata signature of the inherited method implementation that is referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06d81-104">語法</span><span class="sxs-lookup"><span data-stu-id="06d81-104">Syntax</span></span>  
  
```  
HRESULT SetMethodImplFlags (   
    [in]  mdMethodDef   md,   
    [in]  DWORD         dwImplFlags   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="06d81-105">參數</span><span class="sxs-lookup"><span data-stu-id="06d81-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="06d81-106">[in]若要變更方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="06d81-106">[in] The token for the method to be changed.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="06d81-107">[in]值的組合[CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md)列舉，指定方法實作功能。</span><span class="sxs-lookup"><span data-stu-id="06d81-107">[in] A combination of the values of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the method implementation features.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06d81-108">需求</span><span class="sxs-lookup"><span data-stu-id="06d81-108">Requirements</span></span>  
 <span data-ttu-id="06d81-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="06d81-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06d81-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="06d81-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="06d81-111">**程式庫：** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="06d81-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="06d81-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06d81-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06d81-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06d81-113">See also</span></span>
- [<span data-ttu-id="06d81-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="06d81-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="06d81-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="06d81-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
