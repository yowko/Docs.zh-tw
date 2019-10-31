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
ms.openlocfilehash: 4eb6682ac5a8b7788d97f752f249d85886fba0b6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111643"
---
# <a name="iclrdebuggingcanunloadnow-method"></a><span data-ttu-id="917f4-102">ICLRDebugging::CanUnloadNow 方法</span><span class="sxs-lookup"><span data-stu-id="917f4-102">ICLRDebugging::CanUnloadNow Method</span></span>
<span data-ttu-id="917f4-103">判斷[ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)介面所提供的程式庫是否仍在使用中，或是否可以卸載。</span><span class="sxs-lookup"><span data-stu-id="917f4-103">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="917f4-104">語法</span><span class="sxs-lookup"><span data-stu-id="917f4-104">Syntax</span></span>  
  
```cpp  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="917f4-105">參數</span><span class="sxs-lookup"><span data-stu-id="917f4-105">Parameters</span></span>  
 `hmodule`  
 <span data-ttu-id="917f4-106">在目標進程中模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="917f4-106">[in] The base address of a module in the target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="917f4-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="917f4-107">Return Value</span></span>  
 <span data-ttu-id="917f4-108">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="917f4-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="917f4-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="917f4-109">HRESULT</span></span>|<span data-ttu-id="917f4-110">描述</span><span class="sxs-lookup"><span data-stu-id="917f4-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="917f4-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="917f4-111">S_OK</span></span>|<span data-ttu-id="917f4-112">`hmodule` 所參考的模組可以卸載。</span><span class="sxs-lookup"><span data-stu-id="917f4-112">The module that is referenced by `hmodule` can be unloaded.</span></span>|  
|<span data-ttu-id="917f4-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="917f4-113">S_FALSE</span></span>|<span data-ttu-id="917f4-114">`hmodule` 所參考的模組仍在使用中。</span><span class="sxs-lookup"><span data-stu-id="917f4-114">The module that is referenced by `hmodule` is still in use.</span></span>|  
|<span data-ttu-id="917f4-115">COR_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="917f4-115">COR_E_NOT_CLR</span></span>|<span data-ttu-id="917f4-116">指出的模組不是 CLR 模組。</span><span class="sxs-lookup"><span data-stu-id="917f4-116">The indicated module is not a CLR module.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="917f4-117">例外狀況</span><span class="sxs-lookup"><span data-stu-id="917f4-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="917f4-118">備註</span><span class="sxs-lookup"><span data-stu-id="917f4-118">Remarks</span></span>  
 <span data-ttu-id="917f4-119">這個方法會檢查是否已釋放 `ICorDebug*` 介面的所有實例，而且目前沒有任何執行緒在[ICLRDebugging：： OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)方法的呼叫中。</span><span class="sxs-lookup"><span data-stu-id="917f4-119">This method checks to see if all instances of `ICorDebug*` interfaces have been released and no thread is currently within a call to the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="917f4-120">需求</span><span class="sxs-lookup"><span data-stu-id="917f4-120">Requirements</span></span>  
 <span data-ttu-id="917f4-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="917f4-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="917f4-122">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="917f4-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="917f4-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="917f4-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="917f4-124">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="917f4-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="917f4-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="917f4-125">See also</span></span>

- [<span data-ttu-id="917f4-126">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="917f4-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="917f4-127">偵錯</span><span class="sxs-lookup"><span data-stu-id="917f4-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
