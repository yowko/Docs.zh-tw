---
title: IMetaDataEmit::DefineMemberRef 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMemberRef
helpviewer_keywords:
- DefineMemberRef method [.NET Framework metadata]
- IMetaDataEmit::DefineMemberRef method [.NET Framework metadata]
ms.assetid: 21b5bcb8-ea75-4962-8acc-ad17584061e5
topic_type:
- apiref
ms.openlocfilehash: e371330336002c673f2c54d882e70dbed41b743c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175833"
---
# <a name="imetadataemitdefinememberref-method"></a><span data-ttu-id="52958-102">IMetaDataEmit::DefineMemberRef 方法</span><span class="sxs-lookup"><span data-stu-id="52958-102">IMetaDataEmit::DefineMemberRef Method</span></span>
<span data-ttu-id="52958-103">定義對當前作用域之外模組成員的引用，並獲取該引用定義的權杖。</span><span class="sxs-lookup"><span data-stu-id="52958-103">Defines a reference to a member of a module outside the current scope, and gets a token to that reference definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52958-104">語法</span><span class="sxs-lookup"><span data-stu-id="52958-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMemberRef (
    [in]  mdToken           tkImport,
    [in]  LPCWSTR           szName,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMemberRef       *pmr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52958-105">參數</span><span class="sxs-lookup"><span data-stu-id="52958-105">Parameters</span></span>  
 `tkImport`  
 <span data-ttu-id="52958-106">[在]如果成員不是全域的，則目標成員的類或介面的權杖;如果成員是全域的，則`mdModuleRef`該其他檔的權杖。</span><span class="sxs-lookup"><span data-stu-id="52958-106">[in] Token for the target member's class or interface, if the member is not global; if the member is global, the `mdModuleRef` token for that other file.</span></span>  
  
 `szName`  
 <span data-ttu-id="52958-107">[在]目標成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="52958-107">[in] The name of the target member.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="52958-108">[在]目標成員的簽名。</span><span class="sxs-lookup"><span data-stu-id="52958-108">[in] The signature of the target member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="52958-109">[在]中的`pvSigBlob`位元組計數。</span><span class="sxs-lookup"><span data-stu-id="52958-109">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="52958-110">[出]分配的`mdMemberRef`權杖。</span><span class="sxs-lookup"><span data-stu-id="52958-110">[out] The `mdMemberRef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52958-111">需求</span><span class="sxs-lookup"><span data-stu-id="52958-111">Requirements</span></span>  
 <span data-ttu-id="52958-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="52958-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52958-113">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="52958-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="52958-114">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="52958-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="52958-115">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52958-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52958-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52958-116">See also</span></span>

- [<span data-ttu-id="52958-117">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="52958-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="52958-118">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="52958-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
