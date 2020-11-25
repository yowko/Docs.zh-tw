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
ms.openlocfilehash: d355e0e3b2461932384ca11d83d46fd1dc63b80e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732680"
---
# <a name="imetadataemitdeleteclasslayout-method"></a><span data-ttu-id="ec214-102">IMetaDataEmit::DeleteClassLayout 方法</span><span class="sxs-lookup"><span data-stu-id="ec214-102">IMetaDataEmit::DeleteClassLayout Method</span></span>

<span data-ttu-id="ec214-103">終結指定標記所表示之型別的類別配置中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="ec214-103">Destroys the class layout metadata signature for the type represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec214-104">語法</span><span class="sxs-lookup"><span data-stu-id="ec214-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteClassLayout (  
    [in]  mdTypeDef   td  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec214-105">參數</span><span class="sxs-lookup"><span data-stu-id="ec214-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="ec214-106">在 `mdTypeDef` 元資料標記，代表將刪除其類別配置的型別。</span><span class="sxs-lookup"><span data-stu-id="ec214-106">[in] An `mdTypeDef` metadata token that represents the type for which the class layout will be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec214-107">需求</span><span class="sxs-lookup"><span data-stu-id="ec214-107">Requirements</span></span>  

 <span data-ttu-id="ec214-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ec214-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec214-109">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="ec214-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ec214-110">連結 **庫：** 當做 MSCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="ec214-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ec214-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec214-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec214-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec214-112">See also</span></span>

- [<span data-ttu-id="ec214-113">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="ec214-113">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="ec214-114">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="ec214-114">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
