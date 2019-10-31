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
ms.openlocfilehash: 0e54027806cef07fad4740c3bf5226fd26c72570
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108769"
---
# <a name="createassemblyenum-function"></a><span data-ttu-id="eea49-102">CreateAssemblyEnum 函式</span><span class="sxs-lookup"><span data-stu-id="eea49-102">CreateAssemblyEnum Function</span></span>
<span data-ttu-id="eea49-103">取得[IAssemblyEnum](iassemblyenum-interface.md)實例的指標，這個實例可以使用指定的[IAssemblyName](iassemblyname-interface.md)來列舉元件中的物件。</span><span class="sxs-lookup"><span data-stu-id="eea49-103">Gets a pointer to an [IAssemblyEnum](iassemblyenum-interface.md) instance that can enumerate the objects in the assembly with the specified [IAssemblyName](iassemblyname-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eea49-104">語法</span><span class="sxs-lookup"><span data-stu-id="eea49-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="eea49-105">參數</span><span class="sxs-lookup"><span data-stu-id="eea49-105">Parameters</span></span>  
 `pEnum`  
 <span data-ttu-id="eea49-106">脫銷記憶體位置的指標，其中包含所要求的 `IAssemblyEnum` 指標。</span><span class="sxs-lookup"><span data-stu-id="eea49-106">[out] Pointer to a memory location that contains the requested `IAssemblyEnum` pointer.</span></span>  
  
 `pUnkReserved`  
 <span data-ttu-id="eea49-107">在保留以供未來擴充性之用。</span><span class="sxs-lookup"><span data-stu-id="eea49-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="eea49-108">`pUnkReserved` 必須是 null 參考。</span><span class="sxs-lookup"><span data-stu-id="eea49-108">`pUnkReserved` must be a null reference.</span></span>  
  
 `pName`  
 <span data-ttu-id="eea49-109">在所要求之元件的 `IAssemblyName`。</span><span class="sxs-lookup"><span data-stu-id="eea49-109">[in] The `IAssemblyName` of the requested assembly.</span></span> <span data-ttu-id="eea49-110">這個名稱是用來篩選列舉型別。</span><span class="sxs-lookup"><span data-stu-id="eea49-110">This name is used to filter the enumeration.</span></span> <span data-ttu-id="eea49-111">它可以是 null，以列舉全域組件快取中的所有元件。</span><span class="sxs-lookup"><span data-stu-id="eea49-111">It can be null to enumerate all assemblies in the global assembly cache.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="eea49-112">在用來修改列舉值行為的旗標。</span><span class="sxs-lookup"><span data-stu-id="eea49-112">[in] Flags for modifying the enumerator's behavior.</span></span> <span data-ttu-id="eea49-113">此參數只包含[ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md)列舉中的一個位。</span><span class="sxs-lookup"><span data-stu-id="eea49-113">This parameter contains exactly one bit from the [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) enumeration.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="eea49-114">在保留以供未來擴充性之用。</span><span class="sxs-lookup"><span data-stu-id="eea49-114">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="eea49-115">`pvReserved` 必須是 null 參考。</span><span class="sxs-lookup"><span data-stu-id="eea49-115">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eea49-116">備註</span><span class="sxs-lookup"><span data-stu-id="eea49-116">Remarks</span></span>  
 <span data-ttu-id="eea49-117">`dwFlags` 參數包含剛好來自 `ASM_CACHE_FLAGS` 列舉的一個位。</span><span class="sxs-lookup"><span data-stu-id="eea49-117">The `dwFlags` parameter contains exactly one bit from the `ASM_CACHE_FLAGS` enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eea49-118">需求</span><span class="sxs-lookup"><span data-stu-id="eea49-118">Requirements</span></span>  
 <span data-ttu-id="eea49-119">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eea49-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eea49-120">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="eea49-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="eea49-121">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="eea49-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="eea49-122">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eea49-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eea49-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="eea49-123">See also</span></span>

- [<span data-ttu-id="eea49-124">IAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="eea49-124">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
- [<span data-ttu-id="eea49-125">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="eea49-125">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="eea49-126">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="eea49-126">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
