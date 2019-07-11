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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 994f6668de3040cc9f2381356d6db06c18c9e984
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745876"
---
# <a name="iceegentruncatesection-method"></a><span data-ttu-id="6dfac-102">ICeeGen::TruncateSection 方法</span><span class="sxs-lookup"><span data-stu-id="6dfac-102">ICeeGen::TruncateSection Method</span></span>
<span data-ttu-id="6dfac-103">將指定的程式碼區段捨去指定的長度。</span><span class="sxs-lookup"><span data-stu-id="6dfac-103">Truncates the specified code section by the specified length.</span></span>  
  
 <span data-ttu-id="6dfac-104">這個方法已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="6dfac-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dfac-105">語法</span><span class="sxs-lookup"><span data-stu-id="6dfac-105">Syntax</span></span>  
  
```cpp  
HRESULT TruncateSection (  
    [in]  HCEESECTION     section,  
    [in]  ULONG           len  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6dfac-106">參數</span><span class="sxs-lookup"><span data-stu-id="6dfac-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="6dfac-107">[in]要截斷的區段。</span><span class="sxs-lookup"><span data-stu-id="6dfac-107">[in] The section to truncate.</span></span>  
  
 `len`  
 <span data-ttu-id="6dfac-108">[in]以位元組為單位，所要截斷的區段長度。</span><span class="sxs-lookup"><span data-stu-id="6dfac-108">[in] The length, in bytes, by which to truncate the section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6dfac-109">備註</span><span class="sxs-lookup"><span data-stu-id="6dfac-109">Remarks</span></span>  
 <span data-ttu-id="6dfac-110">呼叫`TruncateSection`只有當您有未處理的其他方法的特殊區段需求。</span><span class="sxs-lookup"><span data-stu-id="6dfac-110">Call `TruncateSection` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dfac-111">需求</span><span class="sxs-lookup"><span data-stu-id="6dfac-111">Requirements</span></span>  
 <span data-ttu-id="6dfac-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6dfac-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6dfac-113">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6dfac-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6dfac-114">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6dfac-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6dfac-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6dfac-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dfac-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6dfac-116">See also</span></span>

- [<span data-ttu-id="6dfac-117">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="6dfac-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
