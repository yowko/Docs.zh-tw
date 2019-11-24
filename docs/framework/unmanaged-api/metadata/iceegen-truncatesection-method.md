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
ms.openlocfilehash: 87a70587027f283ef5976089b3f2daf1204e68ec
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426123"
---
# <a name="iceegentruncatesection-method"></a><span data-ttu-id="de951-102">ICeeGen::TruncateSection 方法</span><span class="sxs-lookup"><span data-stu-id="de951-102">ICeeGen::TruncateSection Method</span></span>
<span data-ttu-id="de951-103">Truncates the specified code section by the specified length.</span><span class="sxs-lookup"><span data-stu-id="de951-103">Truncates the specified code section by the specified length.</span></span>  
  
 <span data-ttu-id="de951-104">This method is obsolete and should not be used.</span><span class="sxs-lookup"><span data-stu-id="de951-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de951-105">語法</span><span class="sxs-lookup"><span data-stu-id="de951-105">Syntax</span></span>  
  
```cpp  
HRESULT TruncateSection (  
    [in]  HCEESECTION     section,  
    [in]  ULONG           len  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de951-106">參數</span><span class="sxs-lookup"><span data-stu-id="de951-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="de951-107">[in] The section to truncate.</span><span class="sxs-lookup"><span data-stu-id="de951-107">[in] The section to truncate.</span></span>  
  
 `len`  
 <span data-ttu-id="de951-108">[in] The length, in bytes, by which to truncate the section.</span><span class="sxs-lookup"><span data-stu-id="de951-108">[in] The length, in bytes, by which to truncate the section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de951-109">備註</span><span class="sxs-lookup"><span data-stu-id="de951-109">Remarks</span></span>  
 <span data-ttu-id="de951-110">Call `TruncateSection` only if you have special section requirements that are not handled by other methods.</span><span class="sxs-lookup"><span data-stu-id="de951-110">Call `TruncateSection` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de951-111">需求</span><span class="sxs-lookup"><span data-stu-id="de951-111">Requirements</span></span>  
 <span data-ttu-id="de951-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="de951-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de951-113">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="de951-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="de951-114">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="de951-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="de951-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de951-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de951-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="de951-116">See also</span></span>

- [<span data-ttu-id="de951-117">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="de951-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
