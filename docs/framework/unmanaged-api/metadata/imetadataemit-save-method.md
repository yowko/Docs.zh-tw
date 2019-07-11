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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7ece16d8dcdc685db960a485cd19261f6b9f2fbe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757600"
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="0660e-102">IMetaDataEmit::Save 方法</span><span class="sxs-lookup"><span data-stu-id="0660e-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="0660e-103">將所有的中繼資料儲存在指定的位址檔案目前的範圍中。</span><span class="sxs-lookup"><span data-stu-id="0660e-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0660e-104">語法</span><span class="sxs-lookup"><span data-stu-id="0660e-104">Syntax</span></span>  
  
```cpp  
HRESULT Save (   
    [in]  LPCWSTR     szFile,   
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0660e-105">參數</span><span class="sxs-lookup"><span data-stu-id="0660e-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="0660e-106">[in]若要將儲存至檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="0660e-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="0660e-107">如果此值是 null，記憶體中複本會儲存到最後一個使用的位置。</span><span class="sxs-lookup"><span data-stu-id="0660e-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="0660e-108">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="0660e-108">[in] Reserved.</span></span> <span data-ttu-id="0660e-109">必須是零。</span><span class="sxs-lookup"><span data-stu-id="0660e-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0660e-110">需求</span><span class="sxs-lookup"><span data-stu-id="0660e-110">Requirements</span></span>  
 <span data-ttu-id="0660e-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0660e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0660e-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0660e-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0660e-113">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0660e-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0660e-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0660e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0660e-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0660e-115">See also</span></span>

- [<span data-ttu-id="0660e-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="0660e-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="0660e-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="0660e-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
