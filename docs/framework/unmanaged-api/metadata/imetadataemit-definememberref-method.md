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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 881c0b1f755e750efcc74ca61a60bbd97bc5dba7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444460"
---
# <a name="imetadataemitdefinememberref-method"></a><span data-ttu-id="d3ec6-102">IMetaDataEmit::DefineMemberRef 方法</span><span class="sxs-lookup"><span data-stu-id="d3ec6-102">IMetaDataEmit::DefineMemberRef Method</span></span>
<span data-ttu-id="d3ec6-103">定義目前的範圍外的模組成員的參考，並取得該參考定義的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="d3ec6-103">Defines a reference to a member of a module outside the current scope, and gets a token to that reference definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3ec6-104">語法</span><span class="sxs-lookup"><span data-stu-id="d3ec6-104">Syntax</span></span>  
  
```  
HRESULT DefineMemberRef (   
    [in]  mdToken           tkImport,   
    [in]  LPCWSTR           szName,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [out] mdMemberRef       *pmr   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d3ec6-105">參數</span><span class="sxs-lookup"><span data-stu-id="d3ec6-105">Parameters</span></span>  
 `tkImport`  
 <span data-ttu-id="d3ec6-106">[in]權杖的目標成員的類別或介面，如果成員不是全域的。如果成員是全域`mdModuleRef`權杖以供其他檔案。</span><span class="sxs-lookup"><span data-stu-id="d3ec6-106">[in] Token for the target member's class or interface, if the member is not global; if the member is global, the `mdModuleRef` token for that other file.</span></span>  
  
 `szName`  
 <span data-ttu-id="d3ec6-107">[in]目標成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="d3ec6-107">[in] The name of the target member.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="d3ec6-108">[in]目標成員的簽章。</span><span class="sxs-lookup"><span data-stu-id="d3ec6-108">[in] The signature of the target member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="d3ec6-109">[in]中的位元組計數`pvSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="d3ec6-109">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="d3ec6-110">[out]`mdMemberRef`指派的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="d3ec6-110">[out] The `mdMemberRef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3ec6-111">需求</span><span class="sxs-lookup"><span data-stu-id="d3ec6-111">Requirements</span></span>  
 <span data-ttu-id="d3ec6-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d3ec6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3ec6-113">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d3ec6-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d3ec6-114">**程式庫：** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d3ec6-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3ec6-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3ec6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3ec6-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3ec6-116">See Also</span></span>  
 [<span data-ttu-id="d3ec6-117">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="d3ec6-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="d3ec6-118">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="d3ec6-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
