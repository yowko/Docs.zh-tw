---
title: "IMetaDataEmit::DefineMemberRef 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineMemberRef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineMemberRef
helpviewer_keywords:
- DefineMemberRef method [.NET Framework metadata]
- IMetaDataEmit::DefineMemberRef method [.NET Framework metadata]
ms.assetid: 21b5bcb8-ea75-4962-8acc-ad17584061e5
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4dc4cd317e0e540aaa774cbf9c4c7a2a2ffa40be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinememberref-method"></a><span data-ttu-id="443ba-102">IMetaDataEmit::DefineMemberRef 方法</span><span class="sxs-lookup"><span data-stu-id="443ba-102">IMetaDataEmit::DefineMemberRef Method</span></span>
<span data-ttu-id="443ba-103">定義目前的範圍外的模組成員的參考，並取得該參考定義的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="443ba-103">Defines a reference to a member of a module outside the current scope, and gets a token to that reference definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="443ba-104">語法</span><span class="sxs-lookup"><span data-stu-id="443ba-104">Syntax</span></span>  
  
```  
HRESULT DefineMemberRef (   
    [in]  mdToken           tkImport,   
    [in]  LPCWSTR           szName,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [out] mdMemberRef       *pmr   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="443ba-105">參數</span><span class="sxs-lookup"><span data-stu-id="443ba-105">Parameters</span></span>  
 `tkImport`  
 <span data-ttu-id="443ba-106">[in]權杖的目標成員的類別或介面，如果成員不是全域的。如果成員是全域`mdModuleRef`權杖以供其他檔案。</span><span class="sxs-lookup"><span data-stu-id="443ba-106">[in] Token for the target member's class or interface, if the member is not global; if the member is global, the `mdModuleRef` token for that other file.</span></span>  
  
 `szName`  
 <span data-ttu-id="443ba-107">[in]目標成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="443ba-107">[in] The name of the target member.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="443ba-108">[in]目標成員的簽章。</span><span class="sxs-lookup"><span data-stu-id="443ba-108">[in] The signature of the target member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="443ba-109">[in]中的位元組計數`pvSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="443ba-109">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="443ba-110">[out]`mdMemberRef`指派的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="443ba-110">[out] The `mdMemberRef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="443ba-111">需求</span><span class="sxs-lookup"><span data-stu-id="443ba-111">Requirements</span></span>  
 <span data-ttu-id="443ba-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="443ba-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="443ba-113">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="443ba-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="443ba-114">**程式庫：**做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="443ba-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="443ba-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="443ba-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="443ba-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="443ba-116">See Also</span></span>  
 [<span data-ttu-id="443ba-117">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="443ba-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="443ba-118">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="443ba-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
