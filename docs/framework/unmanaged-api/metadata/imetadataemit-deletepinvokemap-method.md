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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ea100ff86286cb98db5aa9fa6f3c12f5d318a90
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217740"
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="fe126-102">IMetaDataEmit::DeletePinvokeMap 方法</span><span class="sxs-lookup"><span data-stu-id="fe126-102">IMetaDataEmit::DeletePinvokeMap Method</span></span>
<span data-ttu-id="fe126-103">終結指定的語彙基元所參考物件的 PInvoke 對應中繼資料。</span><span class="sxs-lookup"><span data-stu-id="fe126-103">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe126-104">語法</span><span class="sxs-lookup"><span data-stu-id="fe126-104">Syntax</span></span>  
  
```  
HRESULT DeletePinvokeMap (   
    [in]  mdToken     tk   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe126-105">參數</span><span class="sxs-lookup"><span data-stu-id="fe126-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="fe126-106">[in]`mdFieldDef`或`mdMethodDef`語彙基元，表示要刪除的 PInvoke 對應中繼資料物件。</span><span class="sxs-lookup"><span data-stu-id="fe126-106">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe126-107">需求</span><span class="sxs-lookup"><span data-stu-id="fe126-107">Requirements</span></span>  
 <span data-ttu-id="fe126-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fe126-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe126-109">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fe126-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fe126-110">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="fe126-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="fe126-111">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="fe126-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fe126-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe126-112">See also</span></span>

- [<span data-ttu-id="fe126-113">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="fe126-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="fe126-114">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="fe126-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
