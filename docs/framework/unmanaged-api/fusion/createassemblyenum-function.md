---
title: CreateAssemblyEnum 函式
ms.date: 03/30/2017
api_name:
- CreateAssemblyEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyEnum
helpviewer_keywords:
- CreateAssemblyEnum function [.NET Framework fusion]
ms.assetid: 3506df38-6cea-42f6-946e-4287863bcfb3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1db72c44b53b5abff9aee35094abc1e0e577fad4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795382"
---
# <a name="createassemblyenum-function"></a><span data-ttu-id="e28ff-102">CreateAssemblyEnum 函式</span><span class="sxs-lookup"><span data-stu-id="e28ff-102">CreateAssemblyEnum Function</span></span>
<span data-ttu-id="e28ff-103">取得[IAssemblyEnum](iassemblyenum-interface.md)實例的指標，這個實例可以使用指定的[IAssemblyName](iassemblyname-interface.md)來列舉元件中的物件。</span><span class="sxs-lookup"><span data-stu-id="e28ff-103">Gets a pointer to an [IAssemblyEnum](iassemblyenum-interface.md) instance that can enumerate the objects in the assembly with the specified [IAssemblyName](iassemblyname-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e28ff-104">語法</span><span class="sxs-lookup"><span data-stu-id="e28ff-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="e28ff-105">參數</span><span class="sxs-lookup"><span data-stu-id="e28ff-105">Parameters</span></span>  
 `pEnum`  
 <span data-ttu-id="e28ff-106">脫銷包含所要求`IAssemblyEnum`指標之記憶體位置的指標。</span><span class="sxs-lookup"><span data-stu-id="e28ff-106">[out] Pointer to a memory location that contains the requested `IAssemblyEnum` pointer.</span></span>  
  
 `pUnkReserved`  
 <span data-ttu-id="e28ff-107">在保留以供未來擴充性之用。</span><span class="sxs-lookup"><span data-stu-id="e28ff-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="e28ff-108">`pUnkReserved`必須是 null 參考。</span><span class="sxs-lookup"><span data-stu-id="e28ff-108">`pUnkReserved` must be a null reference.</span></span>  
  
 `pName`  
 <span data-ttu-id="e28ff-109">在所`IAssemblyName`要求之元件的。</span><span class="sxs-lookup"><span data-stu-id="e28ff-109">[in] The `IAssemblyName` of the requested assembly.</span></span> <span data-ttu-id="e28ff-110">這個名稱是用來篩選列舉型別。</span><span class="sxs-lookup"><span data-stu-id="e28ff-110">This name is used to filter the enumeration.</span></span> <span data-ttu-id="e28ff-111">它可以是 null，以列舉全域組件快取中的所有元件。</span><span class="sxs-lookup"><span data-stu-id="e28ff-111">It can be null to enumerate all assemblies in the global assembly cache.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="e28ff-112">在用來修改列舉值行為的旗標。</span><span class="sxs-lookup"><span data-stu-id="e28ff-112">[in] Flags for modifying the enumerator's behavior.</span></span> <span data-ttu-id="e28ff-113">此參數只包含[ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md)列舉中的一個位。</span><span class="sxs-lookup"><span data-stu-id="e28ff-113">This parameter contains exactly one bit from the [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) enumeration.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="e28ff-114">在保留以供未來擴充性之用。</span><span class="sxs-lookup"><span data-stu-id="e28ff-114">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="e28ff-115">`pvReserved`必須是 null 參考。</span><span class="sxs-lookup"><span data-stu-id="e28ff-115">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e28ff-116">備註</span><span class="sxs-lookup"><span data-stu-id="e28ff-116">Remarks</span></span>  
 <span data-ttu-id="e28ff-117">參數只包含`ASM_CACHE_FLAGS`列舉中的一個位。 `dwFlags`</span><span class="sxs-lookup"><span data-stu-id="e28ff-117">The `dwFlags` parameter contains exactly one bit from the `ASM_CACHE_FLAGS` enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e28ff-118">需求</span><span class="sxs-lookup"><span data-stu-id="e28ff-118">Requirements</span></span>  
 <span data-ttu-id="e28ff-119">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e28ff-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e28ff-120">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="e28ff-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e28ff-121">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e28ff-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e28ff-122">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e28ff-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e28ff-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e28ff-123">See also</span></span>

- [<span data-ttu-id="e28ff-124">IAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="e28ff-124">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
- [<span data-ttu-id="e28ff-125">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="e28ff-125">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="e28ff-126">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="e28ff-126">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
