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
ms.openlocfilehash: 5ed5afbbf49b6680d00e78b6af3d45c6f0a7229d
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004487"
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="4975a-102">IMetaDataEmit::DefineMethodImpl 方法</span><span class="sxs-lookup"><span data-stu-id="4975a-102">IMetaDataEmit::DefineMethodImpl Method</span></span>
<span data-ttu-id="4975a-103">建立繼承自介面之方法的執行定義，並將權杖傳回給該方法執行定義。</span><span class="sxs-lookup"><span data-stu-id="4975a-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4975a-104">語法</span><span class="sxs-lookup"><span data-stu-id="4975a-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodImpl (
    [in]  mdTypeDef         td,
    [in]  mdToken           tkBody,
    [in]  mdToken           tkDecl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4975a-105">參數</span><span class="sxs-lookup"><span data-stu-id="4975a-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="4975a-106">在`mdTypedef`執行類別的 token。</span><span class="sxs-lookup"><span data-stu-id="4975a-106">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="4975a-107">在程式 `mdMethodDef` `mdMemberRef` 代碼主體的或 token。</span><span class="sxs-lookup"><span data-stu-id="4975a-107">[in] The `mdMethodDef` or `mdMemberRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="4975a-108">在`mdMethodDef` `mdMemberRef` 正在執行之介面方法的或 token。</span><span class="sxs-lookup"><span data-stu-id="4975a-108">[in] The `mdMethodDef` or `mdMemberRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4975a-109">需求</span><span class="sxs-lookup"><span data-stu-id="4975a-109">Requirements</span></span>  
 <span data-ttu-id="4975a-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4975a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4975a-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="4975a-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4975a-112">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="4975a-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4975a-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4975a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4975a-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4975a-114">See also</span></span>

- [<span data-ttu-id="4975a-115">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="4975a-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="4975a-116">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="4975a-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
