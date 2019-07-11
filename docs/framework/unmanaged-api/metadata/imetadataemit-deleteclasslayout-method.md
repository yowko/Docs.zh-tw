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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 84de8e3c688a23198762fca5219d317fabb69c1b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777464"
---
# <a name="imetadataemitdeleteclasslayout-method"></a><span data-ttu-id="83466-102">IMetaDataEmit::DeleteClassLayout 方法</span><span class="sxs-lookup"><span data-stu-id="83466-102">IMetaDataEmit::DeleteClassLayout Method</span></span>
<span data-ttu-id="83466-103">終結指定的語彙基元所代表的型別類別配置中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="83466-103">Destroys the class layout metadata signature for the type represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83466-104">語法</span><span class="sxs-lookup"><span data-stu-id="83466-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteClassLayout (  
    [in]  mdTypeDef   td  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83466-105">參數</span><span class="sxs-lookup"><span data-stu-id="83466-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="83466-106">[in]`mdTypeDef`表示刪除類別配置之類型的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="83466-106">[in] An `mdTypeDef` metadata token that represents the type for which the class layout will be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83466-107">需求</span><span class="sxs-lookup"><span data-stu-id="83466-107">Requirements</span></span>  
 <span data-ttu-id="83466-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="83466-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83466-109">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="83466-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="83466-110">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="83466-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83466-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83466-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83466-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83466-112">See also</span></span>

- [<span data-ttu-id="83466-113">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="83466-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="83466-114">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="83466-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
