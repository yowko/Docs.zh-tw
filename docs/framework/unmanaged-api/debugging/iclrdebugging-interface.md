---
title: ICLRDebugging 介面
ms.date: 03/30/2017
api_name:
- ICLRDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging
helpviewer_keywords:
- ICLRDebugging interface [.NET Framework debugging]
ms.assetid: 429d8fce-b1b1-49d7-895c-28c1c1aa2dbd
topic_type:
- apiref
ms.openlocfilehash: 6506b11d97490f796486729dbeb612e47762b60a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111441"
---
# <a name="iclrdebugging-interface"></a><span data-ttu-id="9e224-102">ICLRDebugging 介面</span><span class="sxs-lookup"><span data-stu-id="9e224-102">ICLRDebugging Interface</span></span>
<span data-ttu-id="9e224-103">提供處理載入及卸載模組以進行偵錯的方法。</span><span class="sxs-lookup"><span data-stu-id="9e224-103">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9e224-104">方法</span><span class="sxs-lookup"><span data-stu-id="9e224-104">Methods</span></span>  
  
|<span data-ttu-id="9e224-105">方法</span><span class="sxs-lookup"><span data-stu-id="9e224-105">Method</span></span>|<span data-ttu-id="9e224-106">描述</span><span class="sxs-lookup"><span data-stu-id="9e224-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9e224-107">OpenVirtualProcess 方法</span><span class="sxs-lookup"><span data-stu-id="9e224-107">OpenVirtualProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)|<span data-ttu-id="9e224-108">取得對應至在進程中載入之 common language runtime （CLR）模組的 "ICorDebugProcess" 介面。</span><span class="sxs-lookup"><span data-stu-id="9e224-108">Gets the "ICorDebugProcess" interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>|  
|[<span data-ttu-id="9e224-109">CanUnloadNow 方法</span><span class="sxs-lookup"><span data-stu-id="9e224-109">CanUnloadNow Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md)|<span data-ttu-id="9e224-110">判斷[ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)介面所提供的程式庫是否仍在使用中，或是否可以卸載。</span><span class="sxs-lookup"><span data-stu-id="9e224-110">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e224-111">備註</span><span class="sxs-lookup"><span data-stu-id="9e224-111">Remarks</span></span>  
 <span data-ttu-id="9e224-112">您可以使用[CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md)函數來取得 `ICLRDebugging` 介面的實例。</span><span class="sxs-lookup"><span data-stu-id="9e224-112">You can obtain an instance of the `ICLRDebugging` interface by using the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e224-113">需求</span><span class="sxs-lookup"><span data-stu-id="9e224-113">Requirements</span></span>  
 <span data-ttu-id="9e224-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9e224-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e224-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e224-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e224-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e224-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e224-117">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e224-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e224-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="9e224-118">See also</span></span>

- [<span data-ttu-id="9e224-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="9e224-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="9e224-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="9e224-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
