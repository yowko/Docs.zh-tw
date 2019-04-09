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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072866"
---
# <a name="iclrdebuggingcanunloadnow-method"></a><span data-ttu-id="368ae-102">ICLRDebugging::CanUnloadNow 方法</span><span class="sxs-lookup"><span data-stu-id="368ae-102">ICLRDebugging::CanUnloadNow Method</span></span>
<span data-ttu-id="368ae-103">決定所提供的程式庫[ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)介面仍在使用或即可予以卸載。</span><span class="sxs-lookup"><span data-stu-id="368ae-103">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="368ae-104">語法</span><span class="sxs-lookup"><span data-stu-id="368ae-104">Syntax</span></span>  
  
```  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="368ae-105">參數</span><span class="sxs-lookup"><span data-stu-id="368ae-105">Parameters</span></span>  
 `hmodule`  
 <span data-ttu-id="368ae-106">[in]目標處理序模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="368ae-106">[in] The base address of a module in the target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="368ae-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="368ae-107">Return Value</span></span>  
 <span data-ttu-id="368ae-108">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="368ae-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="368ae-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="368ae-109">HRESULT</span></span>|<span data-ttu-id="368ae-110">描述</span><span class="sxs-lookup"><span data-stu-id="368ae-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="368ae-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="368ae-111">S_OK</span></span>|<span data-ttu-id="368ae-112">所參考的模組`hmodule`即可予以卸載。</span><span class="sxs-lookup"><span data-stu-id="368ae-112">The module that is referenced by `hmodule` can be unloaded.</span></span>|  
|<span data-ttu-id="368ae-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="368ae-113">S_FALSE</span></span>|<span data-ttu-id="368ae-114">所參考的模組`hmodule`仍在使用中。</span><span class="sxs-lookup"><span data-stu-id="368ae-114">The module that is referenced by `hmodule` is still in use.</span></span>|  
|<span data-ttu-id="368ae-115">COR_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="368ae-115">COR_E_NOT_CLR</span></span>|<span data-ttu-id="368ae-116">指定的模組不是 CLR 模組。</span><span class="sxs-lookup"><span data-stu-id="368ae-116">The indicated module is not a CLR module.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="368ae-117">例外狀況</span><span class="sxs-lookup"><span data-stu-id="368ae-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="368ae-118">備註</span><span class="sxs-lookup"><span data-stu-id="368ae-118">Remarks</span></span>  
 <span data-ttu-id="368ae-119">這個方法會檢查是否所有的執行個體`ICorDebug*`已發行介面，沒有任何執行緒目前的呼叫內[iclrdebugging:: Openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="368ae-119">This method checks to see if all instances of `ICorDebug*` interfaces have been released and no thread is currently within a call to the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="368ae-120">需求</span><span class="sxs-lookup"><span data-stu-id="368ae-120">Requirements</span></span>  
 <span data-ttu-id="368ae-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="368ae-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="368ae-122">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="368ae-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="368ae-123">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="368ae-123">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="368ae-124">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="368ae-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="368ae-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="368ae-125">See also</span></span>

- [<span data-ttu-id="368ae-126">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="368ae-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="368ae-127">偵錯</span><span class="sxs-lookup"><span data-stu-id="368ae-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
