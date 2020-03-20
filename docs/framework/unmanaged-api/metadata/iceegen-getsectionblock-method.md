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
ms.openlocfilehash: a494b1aaa762549528e92ab93d18929ef73eb8da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176080"
---
# <a name="iceegengetsectionblock-method"></a><span data-ttu-id="da6b9-102">ICeeGen::GetSectionBlock 方法</span><span class="sxs-lookup"><span data-stu-id="da6b9-102">ICeeGen::GetSectionBlock Method</span></span>
<span data-ttu-id="da6b9-103">獲取代碼庫的節塊。</span><span class="sxs-lookup"><span data-stu-id="da6b9-103">Gets a section block of the code base.</span></span>  
  
 <span data-ttu-id="da6b9-104">此方法已過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="da6b9-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da6b9-105">語法</span><span class="sxs-lookup"><span data-stu-id="da6b9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="da6b9-106">參數</span><span class="sxs-lookup"><span data-stu-id="da6b9-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="da6b9-107">[在]從中檢索代碼庫塊的部分。</span><span class="sxs-lookup"><span data-stu-id="da6b9-107">[in] The section from which to retrieve a block of the code base.</span></span>  
  
 `len`  
 <span data-ttu-id="da6b9-108">[在]要檢索的塊的長度。</span><span class="sxs-lookup"><span data-stu-id="da6b9-108">[in] The length of the block to be retrieved.</span></span>  
  
 `align`  
 <span data-ttu-id="da6b9-109">[在]相對於節的開頭的位元組，用於對齊塊的第一個位元組。</span><span class="sxs-lookup"><span data-stu-id="da6b9-109">[in] The byte, relative to the beginning of the section, with which to align the first byte of the block.</span></span> <span data-ttu-id="da6b9-110">這是塊在節內的位置。</span><span class="sxs-lookup"><span data-stu-id="da6b9-110">This is the position of the block within the section.</span></span>  
  
 `ppBytes`  
 <span data-ttu-id="da6b9-111">[出]指向接收檢索的塊位址的位置的指標。</span><span class="sxs-lookup"><span data-stu-id="da6b9-111">[out] A pointer to a location that receives the address of the retrieved block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da6b9-112">備註</span><span class="sxs-lookup"><span data-stu-id="da6b9-112">Remarks</span></span>  
 <span data-ttu-id="da6b9-113">僅當`GetSectionBlock`您有特殊節要求時，其他方法未處理，才調用。</span><span class="sxs-lookup"><span data-stu-id="da6b9-113">Call `GetSectionBlock` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da6b9-114">需求</span><span class="sxs-lookup"><span data-stu-id="da6b9-114">Requirements</span></span>  
 <span data-ttu-id="da6b9-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="da6b9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da6b9-116">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="da6b9-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="da6b9-117">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="da6b9-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="da6b9-118">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da6b9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da6b9-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da6b9-119">See also</span></span>

- [<span data-ttu-id="da6b9-120">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="da6b9-120">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
