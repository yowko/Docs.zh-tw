---
title: ICLRDebugging::CanUnloadNow 方法
ms.date: 03/30/2017
api_name:
- ICLRDebugging.CanUnloadNow Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::CanUnloadNow
helpviewer_keywords:
- CanUnloadNow method [.NET Framework debugging]
- ICLRDebugging::CanUnloadNow method [.NET Framework debugging]
ms.assetid: 62e0630c-8cb7-45d2-b622-5a472abfd8cf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80559ef685a2dbf48d65e0d81432a5edbd5528bb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072866"
---
# <a name="iclrdebuggingcanunloadnow-method"></a><span data-ttu-id="cd404-102">ICLRDebugging::CanUnloadNow 方法</span><span class="sxs-lookup"><span data-stu-id="cd404-102">ICLRDebugging::CanUnloadNow Method</span></span>
<span data-ttu-id="cd404-103">決定所提供的程式庫[ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)介面仍在使用或即可予以卸載。</span><span class="sxs-lookup"><span data-stu-id="cd404-103">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd404-104">語法</span><span class="sxs-lookup"><span data-stu-id="cd404-104">Syntax</span></span>  
  
```  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd404-105">參數</span><span class="sxs-lookup"><span data-stu-id="cd404-105">Parameters</span></span>  
 `hmodule`  
 <span data-ttu-id="cd404-106">[in]目標處理序模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="cd404-106">[in] The base address of a module in the target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd404-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="cd404-107">Return Value</span></span>  
 <span data-ttu-id="cd404-108">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="cd404-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="cd404-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cd404-109">HRESULT</span></span>|<span data-ttu-id="cd404-110">描述</span><span class="sxs-lookup"><span data-stu-id="cd404-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cd404-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="cd404-111">S_OK</span></span>|<span data-ttu-id="cd404-112">所參考的模組`hmodule`即可予以卸載。</span><span class="sxs-lookup"><span data-stu-id="cd404-112">The module that is referenced by `hmodule` can be unloaded.</span></span>|  
|<span data-ttu-id="cd404-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="cd404-113">S_FALSE</span></span>|<span data-ttu-id="cd404-114">所參考的模組`hmodule`仍在使用中。</span><span class="sxs-lookup"><span data-stu-id="cd404-114">The module that is referenced by `hmodule` is still in use.</span></span>|  
|<span data-ttu-id="cd404-115">COR_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="cd404-115">COR_E_NOT_CLR</span></span>|<span data-ttu-id="cd404-116">指定的模組不是 CLR 模組。</span><span class="sxs-lookup"><span data-stu-id="cd404-116">The indicated module is not a CLR module.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="cd404-117">例外狀況</span><span class="sxs-lookup"><span data-stu-id="cd404-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd404-118">備註</span><span class="sxs-lookup"><span data-stu-id="cd404-118">Remarks</span></span>  
 <span data-ttu-id="cd404-119">這個方法會檢查是否所有的執行個體`ICorDebug*`已發行介面，沒有任何執行緒目前的呼叫內[iclrdebugging:: Openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="cd404-119">This method checks to see if all instances of `ICorDebug*` interfaces have been released and no thread is currently within a call to the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd404-120">需求</span><span class="sxs-lookup"><span data-stu-id="cd404-120">Requirements</span></span>  
 <span data-ttu-id="cd404-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cd404-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd404-122">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cd404-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cd404-123">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd404-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd404-124">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd404-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd404-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd404-125">See also</span></span>

- [<span data-ttu-id="cd404-126">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="cd404-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="cd404-127">偵錯</span><span class="sxs-lookup"><span data-stu-id="cd404-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
