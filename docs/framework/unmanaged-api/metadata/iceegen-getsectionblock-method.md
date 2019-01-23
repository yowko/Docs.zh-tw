---
title: ICeeGen::GetSectionBlock 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb1268d9fd892a4400491aca7966d81a3e23f9c6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54515348"
---
# <a name="iceegengetsectionblock-method"></a><span data-ttu-id="4c08e-102">ICeeGen::GetSectionBlock 方法</span><span class="sxs-lookup"><span data-stu-id="4c08e-102">ICeeGen::GetSectionBlock Method</span></span>
<span data-ttu-id="4c08e-103">取得區段的區塊程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="4c08e-103">Gets a section block of the code base.</span></span>  
  
 <span data-ttu-id="4c08e-104">這個方法已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="4c08e-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c08e-105">語法</span><span class="sxs-lookup"><span data-stu-id="4c08e-105">Syntax</span></span>  
  
```  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,     
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="4c08e-106">參數</span><span class="sxs-lookup"><span data-stu-id="4c08e-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="4c08e-107">[in]要從中擷取的程式碼基底區塊一節。</span><span class="sxs-lookup"><span data-stu-id="4c08e-107">[in] The section from which to retrieve a block of the code base.</span></span>  
  
 `len`  
 <span data-ttu-id="4c08e-108">[in]要擷取區塊的長度。</span><span class="sxs-lookup"><span data-stu-id="4c08e-108">[in] The length of the block to be retrieved.</span></span>  
  
 `align`  
 <span data-ttu-id="4c08e-109">[in]位元組，相對於區段中，用來對齊第一個位元組區塊的開頭。</span><span class="sxs-lookup"><span data-stu-id="4c08e-109">[in] The byte, relative to the beginning of the section, with which to align the first byte of the block.</span></span> <span data-ttu-id="4c08e-110">這是區塊的一節中的位置。</span><span class="sxs-lookup"><span data-stu-id="4c08e-110">This is the position of the block within the section.</span></span>  
  
 `ppBytes`  
 <span data-ttu-id="4c08e-111">[out]接收擷取區塊位址的位置指標。</span><span class="sxs-lookup"><span data-stu-id="4c08e-111">[out] A pointer to a location that receives the address of the retrieved block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c08e-112">備註</span><span class="sxs-lookup"><span data-stu-id="4c08e-112">Remarks</span></span>  
 <span data-ttu-id="4c08e-113">呼叫`GetSectionBlock`只有當您有未處理的其他方法的特殊區段需求。</span><span class="sxs-lookup"><span data-stu-id="4c08e-113">Call `GetSectionBlock` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c08e-114">需求</span><span class="sxs-lookup"><span data-stu-id="4c08e-114">Requirements</span></span>  
 <span data-ttu-id="4c08e-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4c08e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c08e-116">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4c08e-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4c08e-117">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4c08e-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4c08e-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c08e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c08e-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c08e-119">See also</span></span>
- [<span data-ttu-id="4c08e-120">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="4c08e-120">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
