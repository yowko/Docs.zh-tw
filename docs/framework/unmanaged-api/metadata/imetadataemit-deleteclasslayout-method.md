---
title: IMetaDataEmit::DeleteClassLayout 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteClassLayout
helpviewer_keywords:
- DeleteClassLayout method [.NET Framework metadata]
- IMetaDataEmit::DeleteClassLayout method [.NET Framework metadata]
ms.assetid: 65a4ad49-fa49-4b36-8ed1-76dd6a185ab4
topic_type:
- apiref
ms.openlocfilehash: 00f2aa3364b8b707d4100f8d2574ff3765d106da
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450163"
---
# <a name="imetadataemitdeleteclasslayout-method"></a><span data-ttu-id="ff319-102">IMetaDataEmit::DeleteClassLayout 方法</span><span class="sxs-lookup"><span data-stu-id="ff319-102">IMetaDataEmit::DeleteClassLayout Method</span></span>
<span data-ttu-id="ff319-103">終結由指定標記所表示之類型的類別配置中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="ff319-103">Destroys the class layout metadata signature for the type represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff319-104">語法</span><span class="sxs-lookup"><span data-stu-id="ff319-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteClassLayout (  
    [in]  mdTypeDef   td  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff319-105">參數</span><span class="sxs-lookup"><span data-stu-id="ff319-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="ff319-106">在`mdTypeDef` 的元資料標記，表示將會刪除類別配置的類型。</span><span class="sxs-lookup"><span data-stu-id="ff319-106">[in] An `mdTypeDef` metadata token that represents the type for which the class layout will be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff319-107">需求</span><span class="sxs-lookup"><span data-stu-id="ff319-107">Requirements</span></span>  
 <span data-ttu-id="ff319-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ff319-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff319-109">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="ff319-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ff319-110">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="ff319-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ff319-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff319-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff319-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff319-112">See also</span></span>

- [<span data-ttu-id="ff319-113">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="ff319-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ff319-114">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="ff319-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
