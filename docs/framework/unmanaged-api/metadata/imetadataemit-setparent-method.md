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
ms.openlocfilehash: fdaa6aab28eb82450db7b9f946e033bfad55faf5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446065"
---
# <a name="imetadataemitsetparent-method"></a><span data-ttu-id="6b111-102">IMetaDataEmit::SetParent 方法</span><span class="sxs-lookup"><span data-stu-id="6b111-102">IMetaDataEmit::SetParent Method</span></span>
<span data-ttu-id="6b111-103">建立所指定的成員，在先前呼叫所定義[imetadataemit:: Definememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)，屬於指定的類型，如同在先前呼叫[imetadataemit:: Definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)。</span><span class="sxs-lookup"><span data-stu-id="6b111-103">Establishes that the specified member, as defined by a prior call to [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), is a member of the specified type, as defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b111-104">語法</span><span class="sxs-lookup"><span data-stu-id="6b111-104">Syntax</span></span>  
  
```  
HRESULT SetParent (   
    [in]  mdMemberRef mr,   
    [in]  mdToken     tk   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6b111-105">參數</span><span class="sxs-lookup"><span data-stu-id="6b111-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="6b111-106">[in]`mdMemberRef`接收新的父語彙基元。</span><span class="sxs-lookup"><span data-stu-id="6b111-106">[in] The `mdMemberRef` token to receive a new parent.</span></span>  
  
 `tk`  
 <span data-ttu-id="6b111-107">[in]`mdToken` ，新的父代。</span><span class="sxs-lookup"><span data-stu-id="6b111-107">[in] The `mdToken` for the new parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b111-108">需求</span><span class="sxs-lookup"><span data-stu-id="6b111-108">Requirements</span></span>  
 <span data-ttu-id="6b111-109">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6b111-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b111-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6b111-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6b111-111">**程式庫：** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6b111-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b111-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b111-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b111-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b111-113">See Also</span></span>  
 [<span data-ttu-id="6b111-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="6b111-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="6b111-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="6b111-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
