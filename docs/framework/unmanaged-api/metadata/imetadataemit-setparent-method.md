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
ms.openlocfilehash: 7389e9233fd946cdb2c810bec01cfbfffc8b707d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175599"
---
# <a name="imetadataemitsetparent-method"></a><span data-ttu-id="b56be-102">IMetaDataEmit::SetParent 方法</span><span class="sxs-lookup"><span data-stu-id="b56be-102">IMetaDataEmit::SetParent Method</span></span>
<span data-ttu-id="b56be-103">確定由之前對[IMetaDataEmit：:DefineOfRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)的調用定義的指定成員是指定類型的成員，由之前對[IMetaDataEmit：:DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)的調用定義。</span><span class="sxs-lookup"><span data-stu-id="b56be-103">Establishes that the specified member, as defined by a prior call to [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), is a member of the specified type, as defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b56be-104">語法</span><span class="sxs-lookup"><span data-stu-id="b56be-104">Syntax</span></span>  
  
```cpp  
HRESULT SetParent (
    [in]  mdMemberRef mr,
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b56be-105">參數</span><span class="sxs-lookup"><span data-stu-id="b56be-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="b56be-106">[在]用於`mdMemberRef`接收新父項的權杖。</span><span class="sxs-lookup"><span data-stu-id="b56be-106">[in] The `mdMemberRef` token to receive a new parent.</span></span>  
  
 `tk`  
 <span data-ttu-id="b56be-107">[在]為新`mdToken`父父的 。</span><span class="sxs-lookup"><span data-stu-id="b56be-107">[in] The `mdToken` for the new parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b56be-108">需求</span><span class="sxs-lookup"><span data-stu-id="b56be-108">Requirements</span></span>  
 <span data-ttu-id="b56be-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b56be-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b56be-110">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="b56be-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b56be-111">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b56be-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b56be-112">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b56be-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b56be-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b56be-113">See also</span></span>

- [<span data-ttu-id="b56be-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="b56be-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b56be-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="b56be-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
