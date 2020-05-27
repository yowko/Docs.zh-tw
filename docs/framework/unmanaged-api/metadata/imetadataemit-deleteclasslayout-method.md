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
ms.openlocfilehash: 3ef6b89ed6578d77f30d5e53657b962b200b0ed6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009313"
---
# <a name="imetadataemitdeleteclasslayout-method"></a><span data-ttu-id="a2682-102">IMetaDataEmit::DeleteClassLayout 方法</span><span class="sxs-lookup"><span data-stu-id="a2682-102">IMetaDataEmit::DeleteClassLayout Method</span></span>
<span data-ttu-id="a2682-103">終結由指定標記所表示之類型的類別配置中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="a2682-103">Destroys the class layout metadata signature for the type represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2682-104">語法</span><span class="sxs-lookup"><span data-stu-id="a2682-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteClassLayout (  
    [in]  mdTypeDef   td  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2682-105">參數</span><span class="sxs-lookup"><span data-stu-id="a2682-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="a2682-106">在`mdTypeDef`元資料標記，表示將會刪除其類別配置的類型。</span><span class="sxs-lookup"><span data-stu-id="a2682-106">[in] An `mdTypeDef` metadata token that represents the type for which the class layout will be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2682-107">需求</span><span class="sxs-lookup"><span data-stu-id="a2682-107">Requirements</span></span>  
 <span data-ttu-id="a2682-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a2682-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2682-109">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="a2682-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a2682-110">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="a2682-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a2682-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2682-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2682-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2682-112">See also</span></span>

- [<span data-ttu-id="a2682-113">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="a2682-113">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="a2682-114">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="a2682-114">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
