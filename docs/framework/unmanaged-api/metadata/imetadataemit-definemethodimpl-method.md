---
title: IMetaDataEmit::DefineMethodImpl 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethodImpl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethodImpl
helpviewer_keywords:
- DefineMethodImpl method [.NET Framework metadata]
- IMetaDataEmit::DefineMethodImpl method [.NET Framework metadata]
ms.assetid: 9dcc8b3d-33ee-4c7c-8d6f-322c57b94a0f
topic_type:
- apiref
ms.openlocfilehash: 64d76efa8c2f29fda559e5c84217b865540027ba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175820"
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="4b1f5-102">IMetaDataEmit::DefineMethodImpl 方法</span><span class="sxs-lookup"><span data-stu-id="4b1f5-102">IMetaDataEmit::DefineMethodImpl Method</span></span>
<span data-ttu-id="4b1f5-103">為從介面繼承的方法的實現創建定義，並將權杖返回到該方法實現定義。</span><span class="sxs-lookup"><span data-stu-id="4b1f5-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b1f5-104">語法</span><span class="sxs-lookup"><span data-stu-id="4b1f5-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodImpl (
    [in]  mdTypeDef         td,
    [in]  mdToken           tkBody,
    [in]  mdToken           tkDecl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b1f5-105">參數</span><span class="sxs-lookup"><span data-stu-id="4b1f5-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="4b1f5-106">[在]實現`mdTypedef`類的權杖。</span><span class="sxs-lookup"><span data-stu-id="4b1f5-106">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="4b1f5-107">[在]代碼`mdMethodDef`正文`mdMemberRef`的 或 權杖。</span><span class="sxs-lookup"><span data-stu-id="4b1f5-107">[in] The `mdMethodDef` or `mdMemberRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="4b1f5-108">[在]正在`mdMethodDef`實現的`mdMemberRef`介面方法的 或 權杖。</span><span class="sxs-lookup"><span data-stu-id="4b1f5-108">[in] The `mdMethodDef` or `mdMemberRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b1f5-109">需求</span><span class="sxs-lookup"><span data-stu-id="4b1f5-109">Requirements</span></span>  
 <span data-ttu-id="4b1f5-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4b1f5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b1f5-111">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="4b1f5-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4b1f5-112">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4b1f5-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4b1f5-113">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b1f5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b1f5-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b1f5-114">See also</span></span>

- [<span data-ttu-id="4b1f5-115">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="4b1f5-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="4b1f5-116">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="4b1f5-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
