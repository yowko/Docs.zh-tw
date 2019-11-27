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
ms.openlocfilehash: 99f529a151a42cf4a9ee1f74bd3a76a5b6b1b35f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445270"
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="4e737-102">IMetaDataEmit::DefineMethodImpl 方法</span><span class="sxs-lookup"><span data-stu-id="4e737-102">IMetaDataEmit::DefineMethodImpl Method</span></span>
<span data-ttu-id="4e737-103">建立繼承自介面之方法的執行定義，並將權杖傳回給該方法執行定義。</span><span class="sxs-lookup"><span data-stu-id="4e737-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e737-104">語法</span><span class="sxs-lookup"><span data-stu-id="4e737-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodImpl (   
    [in]  mdTypeDef         td,   
    [in]  mdToken           tkBody,   
    [in]  mdToken           tkDecl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e737-105">參數</span><span class="sxs-lookup"><span data-stu-id="4e737-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="4e737-106">在執行中類別的 `mdTypedef` token。</span><span class="sxs-lookup"><span data-stu-id="4e737-106">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="4e737-107">在程式碼主體的 `mdMethodDef` 或 `mdMemberRef` token。</span><span class="sxs-lookup"><span data-stu-id="4e737-107">[in] The `mdMethodDef` or `mdMemberRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="4e737-108">在正在執行之介面方法的 `mdMethodDef` 或 `mdMemberRef` token。</span><span class="sxs-lookup"><span data-stu-id="4e737-108">[in] The `mdMethodDef` or `mdMemberRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e737-109">需求</span><span class="sxs-lookup"><span data-stu-id="4e737-109">Requirements</span></span>  
 <span data-ttu-id="4e737-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4e737-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e737-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="4e737-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4e737-112">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="4e737-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4e737-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e737-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e737-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e737-114">See also</span></span>

- [<span data-ttu-id="4e737-115">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="4e737-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="4e737-116">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="4e737-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
