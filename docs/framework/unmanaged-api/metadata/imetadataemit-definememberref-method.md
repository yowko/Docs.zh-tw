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
ms.openlocfilehash: d5d386b1d3f95e703cc5d9ad1353ea6b84b5b455
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62043211"
---
# <a name="imetadataemitdefinememberref-method"></a><span data-ttu-id="21c5b-102">IMetaDataEmit::DefineMemberRef 方法</span><span class="sxs-lookup"><span data-stu-id="21c5b-102">IMetaDataEmit::DefineMemberRef Method</span></span>
<span data-ttu-id="21c5b-103">定義目前的範圍外的模組成員的參考，並取得該參考定義的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="21c5b-103">Defines a reference to a member of a module outside the current scope, and gets a token to that reference definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21c5b-104">語法</span><span class="sxs-lookup"><span data-stu-id="21c5b-104">Syntax</span></span>  
  
```  
HRESULT DefineMemberRef (   
    [in]  mdToken           tkImport,   
    [in]  LPCWSTR           szName,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [out] mdMemberRef       *pmr   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21c5b-105">參數</span><span class="sxs-lookup"><span data-stu-id="21c5b-105">Parameters</span></span>  
 `tkImport`  
 <span data-ttu-id="21c5b-106">[in]權杖的目標成員的類別或介面，如果在成員不是全域;如果成員是全域、`mdModuleRef`該其他檔案的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="21c5b-106">[in] Token for the target member's class or interface, if the member is not global; if the member is global, the `mdModuleRef` token for that other file.</span></span>  
  
 `szName`  
 <span data-ttu-id="21c5b-107">[in]將目標成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="21c5b-107">[in] The name of the target member.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="21c5b-108">[in]將目標成員的簽章。</span><span class="sxs-lookup"><span data-stu-id="21c5b-108">[in] The signature of the target member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="21c5b-109">[in]中的位元組計數`pvSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="21c5b-109">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="21c5b-110">[out]`mdMemberRef`指派權杖。</span><span class="sxs-lookup"><span data-stu-id="21c5b-110">[out] The `mdMemberRef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21c5b-111">需求</span><span class="sxs-lookup"><span data-stu-id="21c5b-111">Requirements</span></span>  
 <span data-ttu-id="21c5b-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="21c5b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21c5b-113">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="21c5b-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="21c5b-114">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="21c5b-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21c5b-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21c5b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21c5b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21c5b-116">See also</span></span>

- [<span data-ttu-id="21c5b-117">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="21c5b-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="21c5b-118">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="21c5b-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
