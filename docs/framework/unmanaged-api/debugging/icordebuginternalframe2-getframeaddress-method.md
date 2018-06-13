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
ms.openlocfilehash: d088aaaaa80ee3513a37ea0345d720832504c005
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421144"
---
# <a name="icordebuginternalframe2getframeaddress-method"></a><span data-ttu-id="45855-102">ICorDebugInternalFrame2::GetFrameAddress 方法</span><span class="sxs-lookup"><span data-stu-id="45855-102">ICorDebugInternalFrame2::GetFrameAddress Method</span></span>
<span data-ttu-id="45855-103">傳回內部框架的堆疊位址。</span><span class="sxs-lookup"><span data-stu-id="45855-103">Returns the stack address of the internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45855-104">語法</span><span class="sxs-lookup"><span data-stu-id="45855-104">Syntax</span></span>  
  
```  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="45855-105">參數</span><span class="sxs-lookup"><span data-stu-id="45855-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="45855-106">[out]指標`CORDB_ADDRESS`內部框架。</span><span class="sxs-lookup"><span data-stu-id="45855-106">[out] Pointer to the `CORDB_ADDRESS` for the internal frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45855-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="45855-107">Return Value</span></span>  
 <span data-ttu-id="45855-108">這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="45855-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="45855-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="45855-109">HRESULT</span></span>|<span data-ttu-id="45855-110">描述</span><span class="sxs-lookup"><span data-stu-id="45855-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="45855-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="45855-111">S_OK</span></span>|<span data-ttu-id="45855-112">已成功地傳回內部框架的位址。</span><span class="sxs-lookup"><span data-stu-id="45855-112">The address of the internal frame was successfully returned.</span></span>|  
|<span data-ttu-id="45855-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="45855-113">E_FAIL</span></span>|<span data-ttu-id="45855-114">不會傳回內部框架的位址。</span><span class="sxs-lookup"><span data-stu-id="45855-114">The address of the internal frame could not be returned.</span></span>|  
|<span data-ttu-id="45855-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="45855-115">E_INVALIDARG</span></span>|<span data-ttu-id="45855-116">`pAddress` 為 `null`。</span><span class="sxs-lookup"><span data-stu-id="45855-116">`pAddress` is `null`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45855-117">備註</span><span class="sxs-lookup"><span data-stu-id="45855-117">Remarks</span></span>  
 <span data-ttu-id="45855-118">中傳回的值`pAddress`可用來判斷內部相對於其他框架的堆疊上框架的位置。</span><span class="sxs-lookup"><span data-stu-id="45855-118">The value returned in `pAddress` can be used to determine the location of the internal frame relative to other frames on the stack.</span></span> <span data-ttu-id="45855-119">即使在 IA 64 型電腦，內部框架都位於堆疊，而沒有相對應的指標與備份存放區。</span><span class="sxs-lookup"><span data-stu-id="45855-119">Even on IA-64-based computers, the internal frame lives on the stack only, and there is no corresponding pointer to a backing store.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45855-120">需求</span><span class="sxs-lookup"><span data-stu-id="45855-120">Requirements</span></span>  
 <span data-ttu-id="45855-121">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="45855-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45855-122">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="45855-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45855-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45855-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45855-124">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45855-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45855-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45855-125">See Also</span></span>  
 [<span data-ttu-id="45855-126">ICorDebugInternalFrame2 介面</span><span class="sxs-lookup"><span data-stu-id="45855-126">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 [<span data-ttu-id="45855-127">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="45855-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="45855-128">偵錯</span><span class="sxs-lookup"><span data-stu-id="45855-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
