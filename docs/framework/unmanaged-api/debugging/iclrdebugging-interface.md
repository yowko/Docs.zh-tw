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
ms.openlocfilehash: 12b7fa5e61ba6f967544d8ebeee2f1c6a8d3a7b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405989"
---
# <a name="iclrdebugging-interface"></a><span data-ttu-id="ebca6-102">ICLRDebugging 介面</span><span class="sxs-lookup"><span data-stu-id="ebca6-102">ICLRDebugging Interface</span></span>
<span data-ttu-id="ebca6-103">提供處理載入及卸載模組以進行偵錯的方法。</span><span class="sxs-lookup"><span data-stu-id="ebca6-103">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ebca6-104">方法</span><span class="sxs-lookup"><span data-stu-id="ebca6-104">Methods</span></span>  
  
|<span data-ttu-id="ebca6-105">方法</span><span class="sxs-lookup"><span data-stu-id="ebca6-105">Method</span></span>|<span data-ttu-id="ebca6-106">描述</span><span class="sxs-lookup"><span data-stu-id="ebca6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ebca6-107">OpenVirtualProcess 方法</span><span class="sxs-lookup"><span data-stu-id="ebca6-107">OpenVirtualProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)|<span data-ttu-id="ebca6-108">取得對應至 common language runtime (CLR) 模組載入處理序中的"ICorDebugProcess"介面。</span><span class="sxs-lookup"><span data-stu-id="ebca6-108">Gets the "ICorDebugProcess" interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>|  
|[<span data-ttu-id="ebca6-109">CanUnloadNow 方法</span><span class="sxs-lookup"><span data-stu-id="ebca6-109">CanUnloadNow Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md)|<span data-ttu-id="ebca6-110">決定是否由應用程式提供的文件庫[ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)介面仍在使用或卸載。</span><span class="sxs-lookup"><span data-stu-id="ebca6-110">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebca6-111">備註</span><span class="sxs-lookup"><span data-stu-id="ebca6-111">Remarks</span></span>  
 <span data-ttu-id="ebca6-112">您可以取得的執行個體`ICLRDebugging`介面使用[CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="ebca6-112">You can obtain an instance of the `ICLRDebugging` interface by using the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebca6-113">需求</span><span class="sxs-lookup"><span data-stu-id="ebca6-113">Requirements</span></span>  
 <span data-ttu-id="ebca6-114">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ebca6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebca6-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ebca6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ebca6-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ebca6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ebca6-117">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebca6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebca6-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ebca6-118">See Also</span></span>  
 [<span data-ttu-id="ebca6-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="ebca6-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="ebca6-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="ebca6-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
