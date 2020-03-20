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
ms.openlocfilehash: 3b8aed6522b1c7eb2d8916f71d8a66b367623765
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177600"
---
# <a name="imetadataemitdeletetoken-method"></a><span data-ttu-id="8d99a-102">IMetaDataEmit::DeleteToken 方法</span><span class="sxs-lookup"><span data-stu-id="8d99a-102">IMetaDataEmit::DeleteToken Method</span></span>
<span data-ttu-id="8d99a-103">從當前中繼資料作用域中刪除指定的權杖。</span><span class="sxs-lookup"><span data-stu-id="8d99a-103">Deletes the specified token from the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d99a-104">語法</span><span class="sxs-lookup"><span data-stu-id="8d99a-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteToken (
    [in]  mdToken     tkObj
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d99a-105">參數</span><span class="sxs-lookup"><span data-stu-id="8d99a-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="8d99a-106">[在]要刪除的權杖。</span><span class="sxs-lookup"><span data-stu-id="8d99a-106">[in] The token to be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d99a-107">需求</span><span class="sxs-lookup"><span data-stu-id="8d99a-107">Requirements</span></span>  
 <span data-ttu-id="8d99a-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8d99a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d99a-109">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="8d99a-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8d99a-110">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8d99a-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8d99a-111">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d99a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d99a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d99a-112">See also</span></span>

- [<span data-ttu-id="8d99a-113">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="8d99a-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="8d99a-114">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="8d99a-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
