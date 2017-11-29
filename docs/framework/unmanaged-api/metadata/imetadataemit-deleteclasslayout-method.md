---
title: "IMetaDataEmit::DeleteClassLayout 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DeleteClassLayout
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DeleteClassLayout
helpviewer_keywords:
- DeleteClassLayout method [.NET Framework metadata]
- IMetaDataEmit::DeleteClassLayout method [.NET Framework metadata]
ms.assetid: 65a4ad49-fa49-4b36-8ed1-76dd6a185ab4
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a35606f85e134886addd8b30c240442800a9109e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdeleteclasslayout-method"></a><span data-ttu-id="1581b-102">IMetaDataEmit::DeleteClassLayout 方法</span><span class="sxs-lookup"><span data-stu-id="1581b-102">IMetaDataEmit::DeleteClassLayout Method</span></span>
<span data-ttu-id="1581b-103">終結類別配置中繼資料簽章的指定語彙基元所代表的類型。</span><span class="sxs-lookup"><span data-stu-id="1581b-103">Destroys the class layout metadata signature for the type represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1581b-104">語法</span><span class="sxs-lookup"><span data-stu-id="1581b-104">Syntax</span></span>  
  
```  
HRESULT DeleteClassLayout (  
    [in]  mdTypeDef   td  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1581b-105">參數</span><span class="sxs-lookup"><span data-stu-id="1581b-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="1581b-106">[in]`mdTypeDef`代表刪除類別配置類型的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="1581b-106">[in] An `mdTypeDef` metadata token that represents the type for which the class layout will be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1581b-107">需求</span><span class="sxs-lookup"><span data-stu-id="1581b-107">Requirements</span></span>  
 <span data-ttu-id="1581b-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1581b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1581b-109">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1581b-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1581b-110">**程式庫：**做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1581b-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1581b-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1581b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1581b-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1581b-112">See Also</span></span>  
 [<span data-ttu-id="1581b-113">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="1581b-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="1581b-114">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="1581b-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
