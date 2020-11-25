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
ms.openlocfilehash: 24a7c5bca1287e55f3eb06d63e1fed8da37eb3b0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719563"
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="cc6a8-102">IMetaDataEmit::DefineMethodImpl 方法</span><span class="sxs-lookup"><span data-stu-id="cc6a8-102">IMetaDataEmit::DefineMethodImpl Method</span></span>

<span data-ttu-id="cc6a8-103">建立用來執行繼承自介面之方法的定義，並將標記傳回至該方法執行定義。</span><span class="sxs-lookup"><span data-stu-id="cc6a8-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc6a8-104">語法</span><span class="sxs-lookup"><span data-stu-id="cc6a8-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodImpl (
    [in]  mdTypeDef         td,
    [in]  mdToken           tkBody,
    [in]  mdToken           tkDecl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc6a8-105">參數</span><span class="sxs-lookup"><span data-stu-id="cc6a8-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="cc6a8-106">在 `mdTypedef` 執行類別的 token。</span><span class="sxs-lookup"><span data-stu-id="cc6a8-106">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="cc6a8-107">在程式 `mdMethodDef` `mdMemberRef` 代碼主體的或標記。</span><span class="sxs-lookup"><span data-stu-id="cc6a8-107">[in] The `mdMethodDef` or `mdMemberRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="cc6a8-108">在 `mdMethodDef` `mdMemberRef` 正在執行之介面方法的或標記。</span><span class="sxs-lookup"><span data-stu-id="cc6a8-108">[in] The `mdMethodDef` or `mdMemberRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc6a8-109">需求</span><span class="sxs-lookup"><span data-stu-id="cc6a8-109">Requirements</span></span>  

 <span data-ttu-id="cc6a8-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cc6a8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc6a8-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="cc6a8-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cc6a8-112">連結 **庫：** 當做 MSCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="cc6a8-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cc6a8-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc6a8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc6a8-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc6a8-114">See also</span></span>

- [<span data-ttu-id="cc6a8-115">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="cc6a8-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="cc6a8-116">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="cc6a8-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
