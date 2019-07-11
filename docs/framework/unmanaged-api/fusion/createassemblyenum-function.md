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
ms.openlocfilehash: c56b0168df6e4aee69b5d3e5fbbe027ca2c8974a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778451"
---
# <a name="createassemblyenum-function"></a><span data-ttu-id="2bc08-102">CreateAssemblyEnum 函式</span><span class="sxs-lookup"><span data-stu-id="2bc08-102">CreateAssemblyEnum Function</span></span>
<span data-ttu-id="2bc08-103">取得指標[IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)可以列舉具有指定之組件中的物件的執行個體[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="2bc08-103">Gets a pointer to an [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instance that can enumerate the objects in the assembly with the specified [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bc08-104">語法</span><span class="sxs-lookup"><span data-stu-id="2bc08-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="2bc08-105">參數</span><span class="sxs-lookup"><span data-stu-id="2bc08-105">Parameters</span></span>  
 `pEnum`  
 <span data-ttu-id="2bc08-106">[out]包含要求的記憶體位置指標`IAssemblyEnum`指標。</span><span class="sxs-lookup"><span data-stu-id="2bc08-106">[out] Pointer to a memory location that contains the requested `IAssemblyEnum` pointer.</span></span>  
  
 `pUnkReserved`  
 <span data-ttu-id="2bc08-107">[in]保留供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="2bc08-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="2bc08-108">`pUnkReserved` 必須是 null 參考。</span><span class="sxs-lookup"><span data-stu-id="2bc08-108">`pUnkReserved` must be a null reference.</span></span>  
  
 `pName`  
 <span data-ttu-id="2bc08-109">[in]`IAssemblyName`所要求組件。</span><span class="sxs-lookup"><span data-stu-id="2bc08-109">[in] The `IAssemblyName` of the requested assembly.</span></span> <span data-ttu-id="2bc08-110">這個名稱用來篩選列舉型別。</span><span class="sxs-lookup"><span data-stu-id="2bc08-110">This name is used to filter the enumeration.</span></span> <span data-ttu-id="2bc08-111">它可以是 null，以列舉在全域組件快取中的所有組件。</span><span class="sxs-lookup"><span data-stu-id="2bc08-111">It can be null to enumerate all assemblies in the global assembly cache.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="2bc08-112">[in]修改列舉值的行為的旗標。</span><span class="sxs-lookup"><span data-stu-id="2bc08-112">[in] Flags for modifying the enumerator's behavior.</span></span> <span data-ttu-id="2bc08-113">這個參數會包含只從一個位元[ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="2bc08-113">This parameter contains exactly one bit from the [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) enumeration.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="2bc08-114">[in]保留供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="2bc08-114">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="2bc08-115">`pvReserved` 必須是 null 參考。</span><span class="sxs-lookup"><span data-stu-id="2bc08-115">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2bc08-116">備註</span><span class="sxs-lookup"><span data-stu-id="2bc08-116">Remarks</span></span>  
 <span data-ttu-id="2bc08-117">`dwFlags`參數會包含只從一個位元`ASM_CACHE_FLAGS`列舉型別。</span><span class="sxs-lookup"><span data-stu-id="2bc08-117">The `dwFlags` parameter contains exactly one bit from the `ASM_CACHE_FLAGS` enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bc08-118">需求</span><span class="sxs-lookup"><span data-stu-id="2bc08-118">Requirements</span></span>  
 <span data-ttu-id="2bc08-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2bc08-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bc08-120">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="2bc08-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="2bc08-121">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2bc08-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2bc08-122">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bc08-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bc08-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2bc08-123">See also</span></span>

- [<span data-ttu-id="2bc08-124">IAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="2bc08-124">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
- [<span data-ttu-id="2bc08-125">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="2bc08-125">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="2bc08-126">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="2bc08-126">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
