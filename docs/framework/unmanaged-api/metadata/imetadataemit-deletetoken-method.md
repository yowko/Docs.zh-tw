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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d85fb62936678f830ca7eaf26a97c36be5f23ac8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59138238"
---
# <a name="imetadataemitdeletetoken-method"></a><span data-ttu-id="29ced-102">IMetaDataEmit::DeleteToken 方法</span><span class="sxs-lookup"><span data-stu-id="29ced-102">IMetaDataEmit::DeleteToken Method</span></span>
<span data-ttu-id="29ced-103">從目前的中繼資料範圍中刪除指定的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="29ced-103">Deletes the specified token from the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29ced-104">語法</span><span class="sxs-lookup"><span data-stu-id="29ced-104">Syntax</span></span>  
  
```  
HRESULT DeleteToken (   
    [in]  mdToken     tkObj   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29ced-105">參數</span><span class="sxs-lookup"><span data-stu-id="29ced-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="29ced-106">[in]要刪除的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="29ced-106">[in] The token to be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29ced-107">需求</span><span class="sxs-lookup"><span data-stu-id="29ced-107">Requirements</span></span>  
 <span data-ttu-id="29ced-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="29ced-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29ced-109">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="29ced-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="29ced-110">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="29ced-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="29ced-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29ced-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29ced-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29ced-112">See also</span></span>

- [<span data-ttu-id="29ced-113">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="29ced-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="29ced-114">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="29ced-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
