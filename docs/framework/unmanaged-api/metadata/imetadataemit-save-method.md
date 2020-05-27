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
ms.openlocfilehash: 23f6a301c4c11be92e05dbac0d4f69817d857a28
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003936"
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="d1779-102">IMetaDataEmit::Save 方法</span><span class="sxs-lookup"><span data-stu-id="d1779-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="d1779-103">將目前範圍中的所有中繼資料，儲存至指定位址的檔案。</span><span class="sxs-lookup"><span data-stu-id="d1779-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1779-104">語法</span><span class="sxs-lookup"><span data-stu-id="d1779-104">Syntax</span></span>  
  
```cpp  
HRESULT Save (
    [in]  LPCWSTR     szFile,
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1779-105">參數</span><span class="sxs-lookup"><span data-stu-id="d1779-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="d1779-106">在要儲存的檔案名。</span><span class="sxs-lookup"><span data-stu-id="d1779-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="d1779-107">如果此值為 null，則記憶體中的複本將會儲存到所使用的最後一個位置。</span><span class="sxs-lookup"><span data-stu-id="d1779-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="d1779-108">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="d1779-108">[in] Reserved.</span></span> <span data-ttu-id="d1779-109">必須為零。</span><span class="sxs-lookup"><span data-stu-id="d1779-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1779-110">需求</span><span class="sxs-lookup"><span data-stu-id="d1779-110">Requirements</span></span>  
 <span data-ttu-id="d1779-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d1779-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1779-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="d1779-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d1779-113">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="d1779-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d1779-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1779-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1779-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1779-115">See also</span></span>

- [<span data-ttu-id="d1779-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="d1779-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="d1779-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="d1779-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
