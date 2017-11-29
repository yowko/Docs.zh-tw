---
title: "IMetaDataEmit::SetParent 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetParent
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetParent
helpviewer_keywords:
- SetParent method [.NET Framework metadata]
- IMetaDataEmit::SetParent method [.NET Framework metadata]
ms.assetid: 02a02ff7-ae0e-4692-a20e-372405f23052
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 56436b3801eb55559605f6c875bb6fde84c2db8f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetparent-method"></a><span data-ttu-id="a3250-102">IMetaDataEmit::SetParent 方法</span><span class="sxs-lookup"><span data-stu-id="a3250-102">IMetaDataEmit::SetParent Method</span></span>
<span data-ttu-id="a3250-103">建立所指定的成員，在先前呼叫所定義[imetadataemit:: Definememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)，屬於指定的類型，如同在先前呼叫[imetadataemit:: Definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)。</span><span class="sxs-lookup"><span data-stu-id="a3250-103">Establishes that the specified member, as defined by a prior call to [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), is a member of the specified type, as defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3250-104">語法</span><span class="sxs-lookup"><span data-stu-id="a3250-104">Syntax</span></span>  
  
```  
HRESULT SetParent (   
    [in]  mdMemberRef mr,   
    [in]  mdToken     tk   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a3250-105">參數</span><span class="sxs-lookup"><span data-stu-id="a3250-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="a3250-106">[in]`mdMemberRef`接收新的父語彙基元。</span><span class="sxs-lookup"><span data-stu-id="a3250-106">[in] The `mdMemberRef` token to receive a new parent.</span></span>  
  
 `tk`  
 <span data-ttu-id="a3250-107">[in]`mdToken` ，新的父代。</span><span class="sxs-lookup"><span data-stu-id="a3250-107">[in] The `mdToken` for the new parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3250-108">需求</span><span class="sxs-lookup"><span data-stu-id="a3250-108">Requirements</span></span>  
 <span data-ttu-id="a3250-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a3250-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3250-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a3250-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a3250-111">**程式庫：**做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a3250-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a3250-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3250-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3250-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3250-113">See Also</span></span>  
 [<span data-ttu-id="a3250-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="a3250-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="a3250-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="a3250-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
