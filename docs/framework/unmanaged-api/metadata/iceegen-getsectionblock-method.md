---
title: "ICeeGen::GetSectionBlock 方法"
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
- ICeeGen.GetSectionBlock
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionBlock
helpviewer_keywords:
- GetSectionBlock method [.NET Framework metadata]
- ICeeGen::GetSectionBlock method [.NET Framework metadata]
ms.assetid: 05c78aaf-5bbd-497e-9ae2-55f4fae0c5fb
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9e00d7ae1b110fc9f1e1d41d8c3ddb9427b3d44a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iceegengetsectionblock-method"></a><span data-ttu-id="95f55-102">ICeeGen::GetSectionBlock 方法</span><span class="sxs-lookup"><span data-stu-id="95f55-102">ICeeGen::GetSectionBlock Method</span></span>
<span data-ttu-id="95f55-103">取得區段的區塊程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="95f55-103">Gets a section block of the code base.</span></span>  
  
 <span data-ttu-id="95f55-104">這個方法已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="95f55-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95f55-105">語法</span><span class="sxs-lookup"><span data-stu-id="95f55-105">Syntax</span></span>  
  
```  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,     
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="95f55-106">參數</span><span class="sxs-lookup"><span data-stu-id="95f55-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="95f55-107">[in]要從中擷取的程式碼基底區塊 > 一節。</span><span class="sxs-lookup"><span data-stu-id="95f55-107">[in] The section from which to retrieve a block of the code base.</span></span>  
  
 `len`  
 <span data-ttu-id="95f55-108">[in]要擷取區塊的長度。</span><span class="sxs-lookup"><span data-stu-id="95f55-108">[in] The length of the block to be retrieved.</span></span>  
  
 `align`  
 <span data-ttu-id="95f55-109">[in]相對於開頭的區段中，用來對齊區塊的第一個位元組的位元組。</span><span class="sxs-lookup"><span data-stu-id="95f55-109">[in] The byte, relative to the beginning of the section, with which to align the first byte of the block.</span></span> <span data-ttu-id="95f55-110">這是指區塊的區段內的位置。</span><span class="sxs-lookup"><span data-stu-id="95f55-110">This is the position of the block within the section.</span></span>  
  
 `ppBytes`  
 <span data-ttu-id="95f55-111">[out]接收的擷取區塊位址的位置指標。</span><span class="sxs-lookup"><span data-stu-id="95f55-111">[out] A pointer to a location that receives the address of the retrieved block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95f55-112">備註</span><span class="sxs-lookup"><span data-stu-id="95f55-112">Remarks</span></span>  
 <span data-ttu-id="95f55-113">呼叫`GetSectionBlock`只有當您有不由其他方法處理的特殊區段需求。</span><span class="sxs-lookup"><span data-stu-id="95f55-113">Call `GetSectionBlock` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95f55-114">需求</span><span class="sxs-lookup"><span data-stu-id="95f55-114">Requirements</span></span>  
 <span data-ttu-id="95f55-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="95f55-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95f55-116">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="95f55-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="95f55-117">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="95f55-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="95f55-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95f55-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95f55-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="95f55-119">See Also</span></span>  
 [<span data-ttu-id="95f55-120">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="95f55-120">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
