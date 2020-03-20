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
ms.openlocfilehash: fe0b4b7fef0d05c4acc06dad5bc8a4eaf0722c9c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175573"
---
# <a name="imetadataemitsetrva-method"></a><span data-ttu-id="7bfb1-102">IMetaDataEmit::SetRVA 方法</span><span class="sxs-lookup"><span data-stu-id="7bfb1-102">IMetaDataEmit::SetRVA Method</span></span>
<span data-ttu-id="7bfb1-103">設置指定方法的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="7bfb1-103">Sets the relative virtual address of the specified method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bfb1-104">語法</span><span class="sxs-lookup"><span data-stu-id="7bfb1-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRVA (  
    [in]  mdMethodDef  md,
    [in]  ULONG        ulRVA
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7bfb1-105">參數</span><span class="sxs-lookup"><span data-stu-id="7bfb1-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="7bfb1-106">[在]目標方法或方法實現的權杖。</span><span class="sxs-lookup"><span data-stu-id="7bfb1-106">[in] The token for the target method or method implementation.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="7bfb1-107">[在]代碼或資料區域的位址。</span><span class="sxs-lookup"><span data-stu-id="7bfb1-107">[in] The address of the code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bfb1-108">需求</span><span class="sxs-lookup"><span data-stu-id="7bfb1-108">Requirements</span></span>  
 <span data-ttu-id="7bfb1-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7bfb1-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bfb1-110">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="7bfb1-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7bfb1-111">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7bfb1-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7bfb1-112">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bfb1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bfb1-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7bfb1-113">See also</span></span>

- [<span data-ttu-id="7bfb1-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="7bfb1-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="7bfb1-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="7bfb1-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
