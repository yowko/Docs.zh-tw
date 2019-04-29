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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6edee34c8560c989040475fee4a35c6bd2ddb3e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697988"
---
# <a name="iclrdebugging-interface"></a><span data-ttu-id="f73fc-102">ICLRDebugging 介面</span><span class="sxs-lookup"><span data-stu-id="f73fc-102">ICLRDebugging Interface</span></span>
<span data-ttu-id="f73fc-103">提供處理載入及卸載模組以進行偵錯的方法。</span><span class="sxs-lookup"><span data-stu-id="f73fc-103">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f73fc-104">方法</span><span class="sxs-lookup"><span data-stu-id="f73fc-104">Methods</span></span>  
  
|<span data-ttu-id="f73fc-105">方法</span><span class="sxs-lookup"><span data-stu-id="f73fc-105">Method</span></span>|<span data-ttu-id="f73fc-106">描述</span><span class="sxs-lookup"><span data-stu-id="f73fc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f73fc-107">OpenVirtualProcess 方法</span><span class="sxs-lookup"><span data-stu-id="f73fc-107">OpenVirtualProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)|<span data-ttu-id="f73fc-108">取得對應至 common language runtime (CLR) 模組載入程序中的 「 ICorDebugProcess"介面。</span><span class="sxs-lookup"><span data-stu-id="f73fc-108">Gets the "ICorDebugProcess" interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>|  
|[<span data-ttu-id="f73fc-109">CanUnloadNow 方法</span><span class="sxs-lookup"><span data-stu-id="f73fc-109">CanUnloadNow Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md)|<span data-ttu-id="f73fc-110">決定所提供的程式庫[ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)介面仍在使用或即可予以卸載。</span><span class="sxs-lookup"><span data-stu-id="f73fc-110">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f73fc-111">備註</span><span class="sxs-lookup"><span data-stu-id="f73fc-111">Remarks</span></span>  
 <span data-ttu-id="f73fc-112">您可以取得的執行個體`ICLRDebugging`使用的介面[CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="f73fc-112">You can obtain an instance of the `ICLRDebugging` interface by using the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f73fc-113">需求</span><span class="sxs-lookup"><span data-stu-id="f73fc-113">Requirements</span></span>  
 <span data-ttu-id="f73fc-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f73fc-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f73fc-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f73fc-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f73fc-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f73fc-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f73fc-117">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f73fc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f73fc-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f73fc-118">See also</span></span>

- [<span data-ttu-id="f73fc-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="f73fc-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="f73fc-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="f73fc-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
