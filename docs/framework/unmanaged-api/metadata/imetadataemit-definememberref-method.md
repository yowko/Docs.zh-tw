---
title: "IMetaDataEmit::DefineMemberRef 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 38c2c495bc88dadae2d71b1b3710f30998023516
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinememberref-method"></a><span data-ttu-id="1d288-102">IMetaDataEmit::DefineMemberRef 方法</span><span class="sxs-lookup"><span data-stu-id="1d288-102">IMetaDataEmit::DefineMemberRef Method</span></span>
<span data-ttu-id="1d288-103">定義目前的範圍外的模組成員的參考，並取得該參考定義的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="1d288-103">Defines a reference to a member of a module outside the current scope, and gets a token to that reference definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d288-104">語法</span><span class="sxs-lookup"><span data-stu-id="1d288-104">Syntax</span></span>  
  
```  
HRESULT DefineMemberRef (   
    [in]  mdToken           tkImport,   
    [in]  LPCWSTR           szName,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [out] mdMemberRef       *pmr   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1d288-105">參數</span><span class="sxs-lookup"><span data-stu-id="1d288-105">Parameters</span></span>  
 `tkImport`  
 <span data-ttu-id="1d288-106">[in]權杖的目標成員的類別或介面，如果成員不是全域的。如果成員是全域`mdModuleRef`權杖以供其他檔案。</span><span class="sxs-lookup"><span data-stu-id="1d288-106">[in] Token for the target member's class or interface, if the member is not global; if the member is global, the `mdModuleRef` token for that other file.</span></span>  
  
 `szName`  
 <span data-ttu-id="1d288-107">[in]目標成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="1d288-107">[in] The name of the target member.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="1d288-108">[in]目標成員的簽章。</span><span class="sxs-lookup"><span data-stu-id="1d288-108">[in] The signature of the target member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="1d288-109">[in]中的位元組計數`pvSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="1d288-109">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="1d288-110">[out]`mdMemberRef`指派的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="1d288-110">[out] The `mdMemberRef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d288-111">需求</span><span class="sxs-lookup"><span data-stu-id="1d288-111">Requirements</span></span>  
 <span data-ttu-id="1d288-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1d288-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d288-113">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1d288-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1d288-114">**程式庫：**做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1d288-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1d288-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d288-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d288-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="1d288-116">See Also</span></span>  
 [<span data-ttu-id="1d288-117">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="1d288-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="1d288-118">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="1d288-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
