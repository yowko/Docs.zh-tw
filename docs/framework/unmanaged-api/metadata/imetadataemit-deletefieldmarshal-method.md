---
title: "IMetaDataEmit::DeleteFieldMarshal 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataEmit.DeleteFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteFieldMarshal
helpviewer_keywords:
- IMetaDataEmit::DeleteFieldMarshal method [.NET Framework metadata]
- DeleteFieldMarshal method [.NET Framework metadata]
ms.assetid: 7c75aef9-c742-4b33-a14b-56ff94b0f725
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ce60aace95f4da8c021026cf9bfc6c195de5b05f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdeletefieldmarshal-method"></a><span data-ttu-id="92943-102">IMetaDataEmit::DeleteFieldMarshal 方法</span><span class="sxs-lookup"><span data-stu-id="92943-102">IMetaDataEmit::DeleteFieldMarshal Method</span></span>
<span data-ttu-id="92943-103">終結的 PInvoke 封送處理指定的語彙基元所參考之物件的中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="92943-103">Destroys the PInvoke marshaling metadata signature for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92943-104">語法</span><span class="sxs-lookup"><span data-stu-id="92943-104">Syntax</span></span>  
  
```  
HRESULT DeleteFieldMarshal (  
    [in]  mdToken     tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="92943-105">參數</span><span class="sxs-lookup"><span data-stu-id="92943-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="92943-106">[in]`mdFieldDef`或`mdParamDef`表示的欄位或參數，這是要刪除的封送處理的中繼資料簽章語彙基元。</span><span class="sxs-lookup"><span data-stu-id="92943-106">[in] An `mdFieldDef` or `mdParamDef` token that represents the field or parameter for which to delete the marshaling metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92943-107">需求</span><span class="sxs-lookup"><span data-stu-id="92943-107">Requirements</span></span>  
 <span data-ttu-id="92943-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="92943-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92943-109">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="92943-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="92943-110">**程式庫：**做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="92943-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92943-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92943-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92943-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="92943-112">See Also</span></span>  
 [<span data-ttu-id="92943-113">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="92943-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="92943-114">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="92943-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
