---
title: "IMetaDataEmit::DeletePinvokeMap 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DeletePinvokeMap
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DeletePinvokeMap
helpviewer_keywords:
- IMetaDataEmit::DeletePinvokeMap method [.NET Framework metadata]
- DeletePinvokeMap method [.NET Framework metadata]
ms.assetid: 3c4f6b54-5ce7-4a2a-83e1-6dec16441f50
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1479c3fb19feec0e42ee4aec8544a35ce51350a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="94171-102">IMetaDataEmit::DeletePinvokeMap 方法</span><span class="sxs-lookup"><span data-stu-id="94171-102">IMetaDataEmit::DeletePinvokeMap Method</span></span>
<span data-ttu-id="94171-103">終結 PInvoke 對應中繼資料的指定語彙基元所參考的物件。</span><span class="sxs-lookup"><span data-stu-id="94171-103">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94171-104">語法</span><span class="sxs-lookup"><span data-stu-id="94171-104">Syntax</span></span>  
  
```  
HRESULT DeletePinvokeMap (   
    [in]  mdToken     tk   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="94171-105">參數</span><span class="sxs-lookup"><span data-stu-id="94171-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="94171-106">[in]`mdFieldDef`或`mdMethodDef`語彙基元，代表要刪除的 PInvoke 對應中繼資料的物件。</span><span class="sxs-lookup"><span data-stu-id="94171-106">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94171-107">需求</span><span class="sxs-lookup"><span data-stu-id="94171-107">Requirements</span></span>  
 <span data-ttu-id="94171-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="94171-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94171-109">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="94171-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="94171-110">**程式庫：**做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="94171-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="94171-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94171-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94171-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="94171-112">See Also</span></span>  
 [<span data-ttu-id="94171-113">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="94171-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="94171-114">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="94171-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
