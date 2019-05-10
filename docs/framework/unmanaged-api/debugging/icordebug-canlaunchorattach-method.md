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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c109bab2ecd14e2b698a9b24dace56e986ad5e58
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593525"
---
# <a name="icordebugcanlaunchorattach-method"></a><span data-ttu-id="a7035-102">ICorDebug::CanLaunchOrAttach 方法</span><span class="sxs-lookup"><span data-stu-id="a7035-102">ICorDebug::CanLaunchOrAttach Method</span></span>
<span data-ttu-id="a7035-103">會傳回 HRESULT，指出是否有可能在目前的電腦以及執行階段組態的內容中啟動新的處理序，或附加至指定的現有處理序。</span><span class="sxs-lookup"><span data-stu-id="a7035-103">Returns an HRESULT that indicates whether launching a new process or attaching to the specified existing process is possible within the context of the current machine and runtime configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7035-104">語法</span><span class="sxs-lookup"><span data-stu-id="a7035-104">Syntax</span></span>  
  
```  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7035-105">參數</span><span class="sxs-lookup"><span data-stu-id="a7035-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="a7035-106">[in]現有的處理序的識別碼。</span><span class="sxs-lookup"><span data-stu-id="a7035-106">[in] The ID of an existing process.</span></span>  
  
 `win32DebuggingEnabled`  
 <span data-ttu-id="a7035-107">[in]傳入`true`如果您計劃使用 Win32 啟用偵錯，來啟動或附加啟用，否則，偵錯 Win32 傳遞`false`。</span><span class="sxs-lookup"><span data-stu-id="a7035-107">[in] Pass in `true` if you plan to launch with Win32 debugging enabled, or to attach with Win32 debugging enabled; otherwise, pass `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7035-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="a7035-108">Return Value</span></span>  
 <span data-ttu-id="a7035-109">如果偵錯服務判斷啟動新的處理序，或附加至指定的處理序，為 S_OK 是可行的指定目前的電腦和執行階段組態的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="a7035-109">S_OK if the debugging services determine that launching a new process or attaching to the given process is possible, given the information about the current machine and runtime configuration.</span></span> <span data-ttu-id="a7035-110">可能的 HRESULT 值為：</span><span class="sxs-lookup"><span data-stu-id="a7035-110">Possible HRESULT values are:</span></span>  
  
- <span data-ttu-id="a7035-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a7035-111">S_OK</span></span>  
  
- <span data-ttu-id="a7035-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span><span class="sxs-lookup"><span data-stu-id="a7035-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span></span>  
  
- <span data-ttu-id="a7035-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span><span class="sxs-lookup"><span data-stu-id="a7035-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span></span>  
  
- <span data-ttu-id="a7035-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span><span class="sxs-lookup"><span data-stu-id="a7035-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7035-115">備註</span><span class="sxs-lookup"><span data-stu-id="a7035-115">Remarks</span></span>  
 <span data-ttu-id="a7035-116">這個方法僅供參考。</span><span class="sxs-lookup"><span data-stu-id="a7035-116">This method is purely informational.</span></span> <span data-ttu-id="a7035-117">介面不會停止您無法啟動或附加至處理序，不論值傳回`CanLaunchOrAttach`。</span><span class="sxs-lookup"><span data-stu-id="a7035-117">The interface will not stop you from launching or attaching to a process, regardless of the value returned by `CanLaunchOrAttach`.</span></span>  
  
 <span data-ttu-id="a7035-118">若要啟動已啟用偵錯的 Win32 或附加啟用 Win32 偵錯，則會傳遞`true`針對`win32DebuggingEnabled`。</span><span class="sxs-lookup"><span data-stu-id="a7035-118">If you plan to launch with Win32 debugging enabled or attach with Win32 debugging enabled, pass `true` for `win32DebuggingEnabled`.</span></span> <span data-ttu-id="a7035-119">所傳回的 HRESULT`CanLaunchOrAttach`如果您使用此選項可能會不同。</span><span class="sxs-lookup"><span data-stu-id="a7035-119">The HRESULT returned by `CanLaunchOrAttach` might differ if you use this option.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7035-120">需求</span><span class="sxs-lookup"><span data-stu-id="a7035-120">Requirements</span></span>  
 <span data-ttu-id="a7035-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a7035-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7035-122">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a7035-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7035-123">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7035-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7035-124">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7035-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7035-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7035-125">See also</span></span>

- [<span data-ttu-id="a7035-126">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="a7035-126">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
