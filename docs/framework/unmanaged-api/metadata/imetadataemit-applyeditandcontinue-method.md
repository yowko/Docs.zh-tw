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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: faa9bc412e67e0e49ee969bd8b246a424fe628a0
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2018
ms.locfileid: "42930933"
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="7bd77-102">IMetaDataEmit::ApplyEditAndContinue 方法</span><span class="sxs-lookup"><span data-stu-id="7bd77-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>
<span data-ttu-id="7bd77-103">使用指定的中繼資料所做的變更會更新目前的組件範圍。</span><span class="sxs-lookup"><span data-stu-id="7bd77-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bd77-104">語法</span><span class="sxs-lookup"><span data-stu-id="7bd77-104">Syntax</span></span>  
  
```  
HRESULT ApplyEditAndContinue (   
    [in]  IUnknown    *pImport  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7bd77-105">參數</span><span class="sxs-lookup"><span data-stu-id="7bd77-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="7bd77-106">\[在 \]指標[IUnknown](/cpp/atl/iunknown)表示可攜式執行檔 (PE) 的差異中繼資料物件。</span><span class="sxs-lookup"><span data-stu-id="7bd77-106">\[in\] Pointer to an [IUnknown](/cpp/atl/iunknown) object that represents the delta metadata from the portable executable (PE) file.</span></span>
  
 <span data-ttu-id="7bd77-107">差異中繼資料是包含變更模組的實際中繼資料的複本所做的中繼資料的區塊。</span><span class="sxs-lookup"><span data-stu-id="7bd77-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bd77-108">需求</span><span class="sxs-lookup"><span data-stu-id="7bd77-108">Requirements</span></span>  
 <span data-ttu-id="7bd77-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7bd77-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bd77-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7bd77-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7bd77-111">**程式庫：** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7bd77-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7bd77-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bd77-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bd77-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7bd77-113">See Also</span></span>  
 [<span data-ttu-id="7bd77-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="7bd77-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="7bd77-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="7bd77-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
