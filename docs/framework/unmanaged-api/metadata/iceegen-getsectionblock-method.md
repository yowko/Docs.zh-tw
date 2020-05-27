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
ms.openlocfilehash: ed534890fc90d3b8543a1166c85903f10163f0a8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008314"
---
# <a name="iceegengetsectionblock-method"></a><span data-ttu-id="39753-102">ICeeGen::GetSectionBlock 方法</span><span class="sxs-lookup"><span data-stu-id="39753-102">ICeeGen::GetSectionBlock Method</span></span>
<span data-ttu-id="39753-103">取得程式碼基底的區段區塊。</span><span class="sxs-lookup"><span data-stu-id="39753-103">Gets a section block of the code base.</span></span>  
  
 <span data-ttu-id="39753-104">這個方法已過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="39753-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39753-105">語法</span><span class="sxs-lookup"><span data-stu-id="39753-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="39753-106">參數</span><span class="sxs-lookup"><span data-stu-id="39753-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="39753-107">在要從中取得程式碼基底區塊的區段。</span><span class="sxs-lookup"><span data-stu-id="39753-107">[in] The section from which to retrieve a block of the code base.</span></span>  
  
 `len`  
 <span data-ttu-id="39753-108">在要抓取的區塊長度。</span><span class="sxs-lookup"><span data-stu-id="39753-108">[in] The length of the block to be retrieved.</span></span>  
  
 `align`  
 <span data-ttu-id="39753-109">在相對於區段開頭的位元組，用來對齊區塊的第一個位元組。</span><span class="sxs-lookup"><span data-stu-id="39753-109">[in] The byte, relative to the beginning of the section, with which to align the first byte of the block.</span></span> <span data-ttu-id="39753-110">這是區段內區塊的位置。</span><span class="sxs-lookup"><span data-stu-id="39753-110">This is the position of the block within the section.</span></span>  
  
 `ppBytes`  
 <span data-ttu-id="39753-111">脫銷接收所抓取區塊位址之位置的指標。</span><span class="sxs-lookup"><span data-stu-id="39753-111">[out] A pointer to a location that receives the address of the retrieved block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39753-112">備註</span><span class="sxs-lookup"><span data-stu-id="39753-112">Remarks</span></span>  
 <span data-ttu-id="39753-113">`GetSectionBlock`只有當您有其他方法未處理的特殊區段需求時，才需要呼叫。</span><span class="sxs-lookup"><span data-stu-id="39753-113">Call `GetSectionBlock` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39753-114">需求</span><span class="sxs-lookup"><span data-stu-id="39753-114">Requirements</span></span>  
 <span data-ttu-id="39753-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="39753-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39753-116">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="39753-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="39753-117">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="39753-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="39753-118">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39753-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39753-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39753-119">See also</span></span>

- [<span data-ttu-id="39753-120">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="39753-120">ICeeGen Interface</span></span>](iceegen-interface.md)
