---
title: ICorDebug::CanLaunchOrAttach 方法
ms.date: 03/30/2017
api_name:
- ICorDebug.CanLaunchOrAttach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CanLaunchOrAttach
helpviewer_keywords:
- ICorDebug::CanLaunchOrAttach method [.NET Framework debugging]
- CanLaunchOrAttach method [.NET Framework debugging]
ms.assetid: ca7723db-7c07-4cdd-bd92-fba34928b623
topic_type:
- apiref
ms.openlocfilehash: 28b9fb5a25981e5e37a5f1bbb797baeac45e0028
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793567"
---
# <a name="icordebugcanlaunchorattach-method"></a><span data-ttu-id="7031b-102">ICorDebug::CanLaunchOrAttach 方法</span><span class="sxs-lookup"><span data-stu-id="7031b-102">ICorDebug::CanLaunchOrAttach Method</span></span>
<span data-ttu-id="7031b-103">傳回 HRESULT，指出目前的電腦和執行時間設定的內容中，是否可以啟動新進程或附加至指定的現有進程。</span><span class="sxs-lookup"><span data-stu-id="7031b-103">Returns an HRESULT that indicates whether launching a new process or attaching to the specified existing process is possible within the context of the current machine and runtime configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7031b-104">語法</span><span class="sxs-lookup"><span data-stu-id="7031b-104">Syntax</span></span>  
  
```cpp  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7031b-105">參數</span><span class="sxs-lookup"><span data-stu-id="7031b-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="7031b-106">在現有進程的識別碼。</span><span class="sxs-lookup"><span data-stu-id="7031b-106">[in] The ID of an existing process.</span></span>  
  
 `win32DebuggingEnabled`  
 <span data-ttu-id="7031b-107">在傳入 `true` 如果您打算在啟用 Win32 偵測功能的情況下啟動，或附加至啟用 Win32 偵測，則為。否則，請傳遞 `false`。</span><span class="sxs-lookup"><span data-stu-id="7031b-107">[in] Pass in `true` if you plan to launch with Win32 debugging enabled, or to attach with Win32 debugging enabled; otherwise, pass `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7031b-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="7031b-108">Return Value</span></span>  
 <span data-ttu-id="7031b-109">S_OK 偵錯工具是否可以判斷啟動新進程或附加至給定的進程，並提供目前電腦和執行時間設定的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7031b-109">S_OK if the debugging services determine that launching a new process or attaching to the given process is possible, given the information about the current machine and runtime configuration.</span></span> <span data-ttu-id="7031b-110">可能的 HRESULT 值如下：</span><span class="sxs-lookup"><span data-stu-id="7031b-110">Possible HRESULT values are:</span></span>  
  
- <span data-ttu-id="7031b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7031b-111">S_OK</span></span>  
  
- <span data-ttu-id="7031b-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span><span class="sxs-lookup"><span data-stu-id="7031b-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span></span>  
  
- <span data-ttu-id="7031b-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span><span class="sxs-lookup"><span data-stu-id="7031b-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span></span>  
  
- <span data-ttu-id="7031b-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span><span class="sxs-lookup"><span data-stu-id="7031b-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7031b-115">備註</span><span class="sxs-lookup"><span data-stu-id="7031b-115">Remarks</span></span>  
 <span data-ttu-id="7031b-116">這個方法是單純的資訊。</span><span class="sxs-lookup"><span data-stu-id="7031b-116">This method is purely informational.</span></span> <span data-ttu-id="7031b-117">無論 `CanLaunchOrAttach`傳回的值為何，介面都不會阻止您啟動或附加至進程。</span><span class="sxs-lookup"><span data-stu-id="7031b-117">The interface will not stop you from launching or attaching to a process, regardless of the value returned by `CanLaunchOrAttach`.</span></span>  
  
 <span data-ttu-id="7031b-118">如果您打算在啟用 Win32 偵錯工具的情況下啟動或附加已啟用 Win32 偵錯工具，請傳遞 `true` 以進行 `win32DebuggingEnabled`。</span><span class="sxs-lookup"><span data-stu-id="7031b-118">If you plan to launch with Win32 debugging enabled or attach with Win32 debugging enabled, pass `true` for `win32DebuggingEnabled`.</span></span> <span data-ttu-id="7031b-119">如果您使用此選項，`CanLaunchOrAttach` 所傳回的 HRESULT 可能會有所不同。</span><span class="sxs-lookup"><span data-stu-id="7031b-119">The HRESULT returned by `CanLaunchOrAttach` might differ if you use this option.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7031b-120">需求</span><span class="sxs-lookup"><span data-stu-id="7031b-120">Requirements</span></span>  
 <span data-ttu-id="7031b-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7031b-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7031b-122">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7031b-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7031b-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7031b-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7031b-124">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7031b-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7031b-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="7031b-125">See also</span></span>

- [<span data-ttu-id="7031b-126">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="7031b-126">ICorDebug Interface</span></span>](icordebug-interface.md)
