---
title: IMetaDataEmit::DeletePinvokeMap 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeletePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeletePinvokeMap
helpviewer_keywords:
- IMetaDataEmit::DeletePinvokeMap method [.NET Framework metadata]
- DeletePinvokeMap method [.NET Framework metadata]
ms.assetid: 3c4f6b54-5ce7-4a2a-83e1-6dec16441f50
topic_type:
- apiref
ms.openlocfilehash: 45f40dcd419e8e2fdf8a3349ccc9461854ad9aaf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175729"
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="72a1d-102">IMetaDataEmit::DeletePinvokeMap 方法</span><span class="sxs-lookup"><span data-stu-id="72a1d-102">IMetaDataEmit::DeletePinvokeMap Method</span></span>
<span data-ttu-id="72a1d-103">銷毀指定權杖引用的物件的 PInvoke 映射中繼資料。</span><span class="sxs-lookup"><span data-stu-id="72a1d-103">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72a1d-104">語法</span><span class="sxs-lookup"><span data-stu-id="72a1d-104">Syntax</span></span>  
  
```cpp  
HRESULT DeletePinvokeMap (
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72a1d-105">參數</span><span class="sxs-lookup"><span data-stu-id="72a1d-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="72a1d-106">[在]`mdFieldDef`表示要`mdMethodDef`為其刪除 PInvoke 映射中繼資料的物件的或權杖。</span><span class="sxs-lookup"><span data-stu-id="72a1d-106">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72a1d-107">需求</span><span class="sxs-lookup"><span data-stu-id="72a1d-107">Requirements</span></span>  
 <span data-ttu-id="72a1d-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="72a1d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72a1d-109">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="72a1d-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="72a1d-110">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="72a1d-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="72a1d-111">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72a1d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72a1d-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72a1d-112">See also</span></span>

- [<span data-ttu-id="72a1d-113">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="72a1d-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="72a1d-114">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="72a1d-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
