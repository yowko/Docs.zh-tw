---
title: ICeeGen::TruncateSection 方法
ms.date: 03/30/2017
api_name:
- ICeeGen.TruncateSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::TruncateSection
helpviewer_keywords:
- TruncateSection method [.NET Framework metadata]
- ICeeGen::TruncateSection method [.NET Framework metadata]
ms.assetid: 0451d752-1e5c-4c9a-8bad-6cd35b7ba3df
topic_type:
- apiref
ms.openlocfilehash: 387f5f01f2d2589c0b34e50b69398e1feb0e77e0
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008241"
---
# <a name="iceegentruncatesection-method"></a><span data-ttu-id="2cbad-102">ICeeGen::TruncateSection 方法</span><span class="sxs-lookup"><span data-stu-id="2cbad-102">ICeeGen::TruncateSection Method</span></span>
<span data-ttu-id="2cbad-103">依指定的長度截斷指定的程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="2cbad-103">Truncates the specified code section by the specified length.</span></span>  
  
 <span data-ttu-id="2cbad-104">這個方法已過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="2cbad-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cbad-105">語法</span><span class="sxs-lookup"><span data-stu-id="2cbad-105">Syntax</span></span>  
  
```cpp  
HRESULT TruncateSection (  
    [in]  HCEESECTION     section,  
    [in]  ULONG           len  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2cbad-106">參數</span><span class="sxs-lookup"><span data-stu-id="2cbad-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="2cbad-107">在要截斷的區段。</span><span class="sxs-lookup"><span data-stu-id="2cbad-107">[in] The section to truncate.</span></span>  
  
 `len`  
 <span data-ttu-id="2cbad-108">在用來截斷區段的長度（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="2cbad-108">[in] The length, in bytes, by which to truncate the section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2cbad-109">備註</span><span class="sxs-lookup"><span data-stu-id="2cbad-109">Remarks</span></span>  
 <span data-ttu-id="2cbad-110">`TruncateSection`只有當您有其他方法未處理的特殊區段需求時，才需要呼叫。</span><span class="sxs-lookup"><span data-stu-id="2cbad-110">Call `TruncateSection` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cbad-111">需求</span><span class="sxs-lookup"><span data-stu-id="2cbad-111">Requirements</span></span>  
 <span data-ttu-id="2cbad-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2cbad-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cbad-113">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="2cbad-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2cbad-114">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="2cbad-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2cbad-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cbad-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cbad-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2cbad-116">See also</span></span>

- [<span data-ttu-id="2cbad-117">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="2cbad-117">ICeeGen Interface</span></span>](iceegen-interface.md)
