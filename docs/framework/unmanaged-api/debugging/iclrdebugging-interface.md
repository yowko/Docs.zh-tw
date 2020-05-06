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
ms.openlocfilehash: a3d4297e3b16dd1637e6293dbf7f04d4fbeda50f
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860391"
---
# <a name="iclrdebugging-interface"></a><span data-ttu-id="4e702-102">ICLRDebugging 介面</span><span class="sxs-lookup"><span data-stu-id="4e702-102">ICLRDebugging Interface</span></span>
<span data-ttu-id="4e702-103">提供處理載入及卸載模組以進行偵錯的方法。</span><span class="sxs-lookup"><span data-stu-id="4e702-103">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4e702-104">方法</span><span class="sxs-lookup"><span data-stu-id="4e702-104">Methods</span></span>  
  
|<span data-ttu-id="4e702-105">方法</span><span class="sxs-lookup"><span data-stu-id="4e702-105">Method</span></span>|<span data-ttu-id="4e702-106">描述</span><span class="sxs-lookup"><span data-stu-id="4e702-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4e702-107">OpenVirtualProcess 方法</span><span class="sxs-lookup"><span data-stu-id="4e702-107">OpenVirtualProcess Method</span></span>](iclrdebugging-openvirtualprocess-method.md)|<span data-ttu-id="4e702-108">取得對應至在進程中載入之 common language runtime （CLR）模組的 "ICorDebugProcess" 介面。</span><span class="sxs-lookup"><span data-stu-id="4e702-108">Gets the "ICorDebugProcess" interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>|  
|[<span data-ttu-id="4e702-109">CanUnloadNow 方法</span><span class="sxs-lookup"><span data-stu-id="4e702-109">CanUnloadNow Method</span></span>](iclrdebugging-canunloadnow-method.md)|<span data-ttu-id="4e702-110">判斷[ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md)介面所提供的程式庫是否仍在使用中，或是否可以卸載。</span><span class="sxs-lookup"><span data-stu-id="4e702-110">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e702-111">備註</span><span class="sxs-lookup"><span data-stu-id="4e702-111">Remarks</span></span>  
 <span data-ttu-id="4e702-112">您可以使用[CLRCreateInstance](../hosting/clrcreateinstance-function.md)函數來取得`ICLRDebugging`介面的實例。</span><span class="sxs-lookup"><span data-stu-id="4e702-112">You can obtain an instance of the `ICLRDebugging` interface by using the [CLRCreateInstance](../hosting/clrcreateinstance-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e702-113">需求</span><span class="sxs-lookup"><span data-stu-id="4e702-113">Requirements</span></span>  
 <span data-ttu-id="4e702-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4e702-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e702-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4e702-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e702-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e702-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e702-117">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e702-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e702-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="4e702-118">See also</span></span>

- [<span data-ttu-id="4e702-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="4e702-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="4e702-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="4e702-120">Debugging</span></span>](index.md)
