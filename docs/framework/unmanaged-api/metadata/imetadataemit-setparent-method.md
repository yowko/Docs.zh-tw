---
title: IMetaDataEmit::SetParent 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParent
helpviewer_keywords:
- SetParent method [.NET Framework metadata]
- IMetaDataEmit::SetParent method [.NET Framework metadata]
ms.assetid: 02a02ff7-ae0e-4692-a20e-372405f23052
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fe27d8a0508a13c1f54eef00d5119bec4daec4a7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59140435"
---
# <a name="imetadataemitsetparent-method"></a><span data-ttu-id="0b722-102">IMetaDataEmit::SetParent 方法</span><span class="sxs-lookup"><span data-stu-id="0b722-102">IMetaDataEmit::SetParent Method</span></span>
<span data-ttu-id="0b722-103">建立所指定的成員，由先前呼叫所定義[imetadataemit:: Definememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)，是由先前呼叫定義的指定類型的成員[imetadataemit:: Definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)。</span><span class="sxs-lookup"><span data-stu-id="0b722-103">Establishes that the specified member, as defined by a prior call to [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), is a member of the specified type, as defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b722-104">語法</span><span class="sxs-lookup"><span data-stu-id="0b722-104">Syntax</span></span>  
  
```  
HRESULT SetParent (   
    [in]  mdMemberRef mr,   
    [in]  mdToken     tk   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b722-105">參數</span><span class="sxs-lookup"><span data-stu-id="0b722-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="0b722-106">[in]`mdMemberRef`接收新的父項的權杖。</span><span class="sxs-lookup"><span data-stu-id="0b722-106">[in] The `mdMemberRef` token to receive a new parent.</span></span>  
  
 `tk`  
 <span data-ttu-id="0b722-107">[in]`mdToken` ，新的父代。</span><span class="sxs-lookup"><span data-stu-id="0b722-107">[in] The `mdToken` for the new parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b722-108">需求</span><span class="sxs-lookup"><span data-stu-id="0b722-108">Requirements</span></span>  
 <span data-ttu-id="0b722-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0b722-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b722-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0b722-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0b722-111">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0b722-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0b722-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b722-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b722-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b722-113">See also</span></span>

- [<span data-ttu-id="0b722-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="0b722-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="0b722-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="0b722-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
