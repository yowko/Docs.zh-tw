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
ms.openlocfilehash: 7ce9ac95c7183a7d47c367914d80f77c57dde0d7
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005761"
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="3161a-102">IMetaDataEmit::ApplyEditAndContinue 方法</span><span class="sxs-lookup"><span data-stu-id="3161a-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>
<span data-ttu-id="3161a-103">使用在指定的中繼資料中所做的變更，更新目前的元件範圍。</span><span class="sxs-lookup"><span data-stu-id="3161a-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3161a-104">語法</span><span class="sxs-lookup"><span data-stu-id="3161a-104">Syntax</span></span>  
  
```cpp  
HRESULT ApplyEditAndContinue (
    [in]  IUnknown    *pImport  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3161a-105">參數</span><span class="sxs-lookup"><span data-stu-id="3161a-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="3161a-106">\[在 \] [IUnknown](/cpp/atl/iunknown)物件的指標中，代表可移植執行檔（PE）檔案的差異中繼資料。</span><span class="sxs-lookup"><span data-stu-id="3161a-106">\[in\] Pointer to an [IUnknown](/cpp/atl/iunknown) object that represents the delta metadata from the portable executable (PE) file.</span></span>
  
 <span data-ttu-id="3161a-107">差異中繼資料是中繼資料的區塊，其中包含對模組的實際中繼資料之複本所做的變更。</span><span class="sxs-lookup"><span data-stu-id="3161a-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3161a-108">需求</span><span class="sxs-lookup"><span data-stu-id="3161a-108">Requirements</span></span>  
 <span data-ttu-id="3161a-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3161a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3161a-110">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="3161a-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3161a-111">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="3161a-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3161a-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3161a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3161a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3161a-113">See also</span></span>

- [<span data-ttu-id="3161a-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="3161a-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="3161a-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="3161a-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
