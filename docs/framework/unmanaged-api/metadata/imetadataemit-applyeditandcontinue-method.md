---
title: IMetaDataEmit::ApplyEditAndContinue 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.ApplyEditAndContinue
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::ApplyEditAndContinue
helpviewer_keywords:
- ApplyEditAndContinue method [.NET Framework metadata]
- IMetaDataEmit::ApplyEditAndContinue method [.NET Framework metadata]
ms.assetid: 35991289-f389-495d-8caa-a6384fb1d557
topic_type:
- apiref
ms.openlocfilehash: b9cad4c9647983e5b39f9b7a5d03736f2848e1c9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432691"
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="1c520-102">IMetaDataEmit::ApplyEditAndContinue 方法</span><span class="sxs-lookup"><span data-stu-id="1c520-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>
<span data-ttu-id="1c520-103">Updates the current assembly scope with the changes made in the specified metadata.</span><span class="sxs-lookup"><span data-stu-id="1c520-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c520-104">語法</span><span class="sxs-lookup"><span data-stu-id="1c520-104">Syntax</span></span>  
  
```cpp  
HRESULT ApplyEditAndContinue (   
    [in]  IUnknown    *pImport  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c520-105">參數</span><span class="sxs-lookup"><span data-stu-id="1c520-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="1c520-106">\[in\] Pointer to an [IUnknown](/cpp/atl/iunknown) object that represents the delta metadata from the portable executable (PE) file.</span><span class="sxs-lookup"><span data-stu-id="1c520-106">\[in\] Pointer to an [IUnknown](/cpp/atl/iunknown) object that represents the delta metadata from the portable executable (PE) file.</span></span>
  
 <span data-ttu-id="1c520-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span><span class="sxs-lookup"><span data-stu-id="1c520-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c520-108">需求</span><span class="sxs-lookup"><span data-stu-id="1c520-108">Requirements</span></span>  
 <span data-ttu-id="1c520-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1c520-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c520-110">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1c520-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1c520-111">**Library:** Used as a resource in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1c520-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1c520-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c520-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c520-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="1c520-113">See also</span></span>

- [<span data-ttu-id="1c520-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="1c520-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="1c520-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="1c520-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
