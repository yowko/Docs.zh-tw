---
title: IMetaDataEmit::Save 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Save
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Save
helpviewer_keywords:
- Save method, IMetaDataEmit interface [.NET Framework metadata]
- IMetaDataEmit::Save method [.NET Framework metadata]
ms.assetid: c1de8400-adfe-4a71-b828-a1d0cc1ea505
topic_type:
- apiref
ms.openlocfilehash: afd60cdf566bea459816ee890d44cc09258de516
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435941"
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="dbda1-102">IMetaDataEmit::Save 方法</span><span class="sxs-lookup"><span data-stu-id="dbda1-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="dbda1-103">將目前範圍中的所有中繼資料，儲存至指定位址的檔案。</span><span class="sxs-lookup"><span data-stu-id="dbda1-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbda1-104">語法</span><span class="sxs-lookup"><span data-stu-id="dbda1-104">Syntax</span></span>  
  
```cpp  
HRESULT Save (   
    [in]  LPCWSTR     szFile,   
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dbda1-105">參數</span><span class="sxs-lookup"><span data-stu-id="dbda1-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="dbda1-106">在要儲存的檔案名。</span><span class="sxs-lookup"><span data-stu-id="dbda1-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="dbda1-107">如果此值為 null，則記憶體中的複本將會儲存到所使用的最後一個位置。</span><span class="sxs-lookup"><span data-stu-id="dbda1-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="dbda1-108">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="dbda1-108">[in] Reserved.</span></span> <span data-ttu-id="dbda1-109">必須為零。</span><span class="sxs-lookup"><span data-stu-id="dbda1-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbda1-110">需求</span><span class="sxs-lookup"><span data-stu-id="dbda1-110">Requirements</span></span>  
 <span data-ttu-id="dbda1-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dbda1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbda1-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="dbda1-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dbda1-113">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="dbda1-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dbda1-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbda1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbda1-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dbda1-115">See also</span></span>

- [<span data-ttu-id="dbda1-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="dbda1-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="dbda1-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="dbda1-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
