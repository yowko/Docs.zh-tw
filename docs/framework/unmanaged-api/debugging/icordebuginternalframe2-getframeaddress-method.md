---
title: ICorDebugInternalFrame2::GetFrameAddress 方法
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2.GetFrameAddress Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2::GetFrameAddress
helpviewer_keywords:
- GetFrameAddress method [.NET Framework debugging]
- ICorDebugInternalFrame2::GetFrameAddress method [.NET Framework debugging]
ms.assetid: 4ee8d058-ffc8-4967-9133-a5adfef4e518
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3062e636921ea959716a500dae689fbe07915006
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759994"
---
# <a name="icordebuginternalframe2getframeaddress-method"></a><span data-ttu-id="98a1f-102">ICorDebugInternalFrame2::GetFrameAddress 方法</span><span class="sxs-lookup"><span data-stu-id="98a1f-102">ICorDebugInternalFrame2::GetFrameAddress Method</span></span>
<span data-ttu-id="98a1f-103">傳回內部框架的堆疊位址。</span><span class="sxs-lookup"><span data-stu-id="98a1f-103">Returns the stack address of the internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98a1f-104">語法</span><span class="sxs-lookup"><span data-stu-id="98a1f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98a1f-105">參數</span><span class="sxs-lookup"><span data-stu-id="98a1f-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="98a1f-106">[out]指標`CORDB_ADDRESS`內部框架。</span><span class="sxs-lookup"><span data-stu-id="98a1f-106">[out] Pointer to the `CORDB_ADDRESS` for the internal frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="98a1f-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="98a1f-107">Return Value</span></span>  
 <span data-ttu-id="98a1f-108">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="98a1f-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="98a1f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="98a1f-109">HRESULT</span></span>|<span data-ttu-id="98a1f-110">說明</span><span class="sxs-lookup"><span data-stu-id="98a1f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="98a1f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="98a1f-111">S_OK</span></span>|<span data-ttu-id="98a1f-112">已成功地傳回內部框架的位址。</span><span class="sxs-lookup"><span data-stu-id="98a1f-112">The address of the internal frame was successfully returned.</span></span>|  
|<span data-ttu-id="98a1f-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="98a1f-113">E_FAIL</span></span>|<span data-ttu-id="98a1f-114">不會傳回內部框架的位址。</span><span class="sxs-lookup"><span data-stu-id="98a1f-114">The address of the internal frame could not be returned.</span></span>|  
|<span data-ttu-id="98a1f-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="98a1f-115">E_INVALIDARG</span></span>|<span data-ttu-id="98a1f-116">`pAddress` 為 `null`。</span><span class="sxs-lookup"><span data-stu-id="98a1f-116">`pAddress` is `null`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98a1f-117">備註</span><span class="sxs-lookup"><span data-stu-id="98a1f-117">Remarks</span></span>  
 <span data-ttu-id="98a1f-118">中傳回的值`pAddress`可用來判斷內部相對於其他框架在堆疊上框架的位置。</span><span class="sxs-lookup"><span data-stu-id="98a1f-118">The value returned in `pAddress` can be used to determine the location of the internal frame relative to other frames on the stack.</span></span> <span data-ttu-id="98a1f-119">即使在 IA-64 為主的電腦內部框架都位於堆疊，而沒有備份存放區相對應的指標。</span><span class="sxs-lookup"><span data-stu-id="98a1f-119">Even on IA-64-based computers, the internal frame lives on the stack only, and there is no corresponding pointer to a backing store.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98a1f-120">需求</span><span class="sxs-lookup"><span data-stu-id="98a1f-120">Requirements</span></span>  
 <span data-ttu-id="98a1f-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="98a1f-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98a1f-122">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98a1f-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98a1f-123">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98a1f-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98a1f-124">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98a1f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98a1f-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98a1f-125">See also</span></span>

- [<span data-ttu-id="98a1f-126">ICorDebugInternalFrame2 介面</span><span class="sxs-lookup"><span data-stu-id="98a1f-126">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)
- [<span data-ttu-id="98a1f-127">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="98a1f-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="98a1f-128">偵錯</span><span class="sxs-lookup"><span data-stu-id="98a1f-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
