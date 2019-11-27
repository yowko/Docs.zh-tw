---
title: IMetaDataEmit::DeleteToken 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteToken
helpviewer_keywords:
- DeleteToken method [.NET Framework metadata]
- IMetaDataEmit::DeleteToken method [.NET Framework metadata]
ms.assetid: a4926d0a-261b-46b1-9994-82633661a64b
topic_type:
- apiref
ms.openlocfilehash: e8c145632911817e8e19d587bb8afead0a6c33af
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434343"
---
# <a name="imetadataemitdeletetoken-method"></a><span data-ttu-id="ae1ea-102">IMetaDataEmit::DeleteToken 方法</span><span class="sxs-lookup"><span data-stu-id="ae1ea-102">IMetaDataEmit::DeleteToken Method</span></span>
<span data-ttu-id="ae1ea-103">從目前的中繼資料範圍中刪除指定的標記。</span><span class="sxs-lookup"><span data-stu-id="ae1ea-103">Deletes the specified token from the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae1ea-104">語法</span><span class="sxs-lookup"><span data-stu-id="ae1ea-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteToken (   
    [in]  mdToken     tkObj   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae1ea-105">參數</span><span class="sxs-lookup"><span data-stu-id="ae1ea-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="ae1ea-106">在要刪除的 token。</span><span class="sxs-lookup"><span data-stu-id="ae1ea-106">[in] The token to be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae1ea-107">需求</span><span class="sxs-lookup"><span data-stu-id="ae1ea-107">Requirements</span></span>  
 <span data-ttu-id="ae1ea-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ae1ea-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae1ea-109">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="ae1ea-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ae1ea-110">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="ae1ea-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ae1ea-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae1ea-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae1ea-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae1ea-112">See also</span></span>

- [<span data-ttu-id="ae1ea-113">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="ae1ea-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ae1ea-114">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="ae1ea-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
