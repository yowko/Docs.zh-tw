---
title: IMetaDataEmit::SetFieldRVA 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldRVA
helpviewer_keywords:
- IMetaDataEmit::SetFieldRVA method [.NET Framework metadata]
- SetFieldRVA method [.NET Framework metadata]
ms.assetid: 6dc37f9d-87ee-4cb3-9216-ced600184ce8
topic_type:
- apiref
ms.openlocfilehash: 501199bedec3b7a65d95c80cdef178831a65fd01
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428413"
---
# <a name="imetadataemitsetfieldrva-method"></a><span data-ttu-id="e77be-102">IMetaDataEmit::SetFieldRVA 方法</span><span class="sxs-lookup"><span data-stu-id="e77be-102">IMetaDataEmit::SetFieldRVA Method</span></span>
<span data-ttu-id="e77be-103">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span><span class="sxs-lookup"><span data-stu-id="e77be-103">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e77be-104">語法</span><span class="sxs-lookup"><span data-stu-id="e77be-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldRVA (   
    [in]  mdFieldDef  fd,   
    [in]  ULONG       ulRVA   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e77be-105">參數</span><span class="sxs-lookup"><span data-stu-id="e77be-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="e77be-106">[in] The token for the target field.</span><span class="sxs-lookup"><span data-stu-id="e77be-106">[in] The token for the target field.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="e77be-107">[in] The address of a code or data area.</span><span class="sxs-lookup"><span data-stu-id="e77be-107">[in] The address of a code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e77be-108">需求</span><span class="sxs-lookup"><span data-stu-id="e77be-108">Requirements</span></span>  
 <span data-ttu-id="e77be-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e77be-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e77be-110">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e77be-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e77be-111">**Library:** Used as a resource in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e77be-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e77be-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e77be-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e77be-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="e77be-113">See also</span></span>

- [<span data-ttu-id="e77be-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="e77be-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="e77be-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="e77be-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
