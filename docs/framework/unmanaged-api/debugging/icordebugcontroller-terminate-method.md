---
title: ICorDebugController::Terminate 方法
ms.date: 03/30/2017
api_name:
- ICorDebugController.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Terminate
helpviewer_keywords:
- Terminate method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Terminate method [.NET Framework debugging]
ms.assetid: 4275af0c-b5a7-4e4c-97c9-7e41f36b2dd8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 362ae813846ab31f170ae49288735996eb1e9555
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531755"
---
# <a name="icordebugcontrollerterminate-method"></a><span data-ttu-id="ccced-102">ICorDebugController::Terminate 方法</span><span class="sxs-lookup"><span data-stu-id="ccced-102">ICorDebugController::Terminate Method</span></span>
<span data-ttu-id="ccced-103">終止與指定的結束代碼的程序。</span><span class="sxs-lookup"><span data-stu-id="ccced-103">Terminates the process with the specified exit code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ccced-104">這個方法是 Win32 的包裝函式`TerminateProcess`函式。</span><span class="sxs-lookup"><span data-stu-id="ccced-104">This method is a wrapper for the Win32 `TerminateProcess` function.</span></span> <span data-ttu-id="ccced-105">因此，`Terminate`會結束程式碼使用相同方式來 Win32`TerminateProcess`函式會使用它。</span><span class="sxs-lookup"><span data-stu-id="ccced-105">Thus, `Terminate` uses the exit code in the same way that the Win32 `TerminateProcess` function uses it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccced-106">語法</span><span class="sxs-lookup"><span data-stu-id="ccced-106">Syntax</span></span>  
  
```  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ccced-107">參數</span><span class="sxs-lookup"><span data-stu-id="ccced-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="ccced-108">[in]結束代碼數字值。</span><span class="sxs-lookup"><span data-stu-id="ccced-108">[in] A numeric value that is the exit code.</span></span> <span data-ttu-id="ccced-109">Winbase.h 中定義之有效的數字值。</span><span class="sxs-lookup"><span data-stu-id="ccced-109">The valid numeric values are defined in Winbase.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ccced-110">備註</span><span class="sxs-lookup"><span data-stu-id="ccced-110">Remarks</span></span>  
 <span data-ttu-id="ccced-111">如果處理程序已停止的時機`Terminate`是呼叫，應該會繼續執行處理序使用[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)方法，讓偵錯工具會收到確認透過終止[Icordebugmanagedcallback:: Exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)或是[icordebugmanagedcallback:: Exitappdomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="ccced-111">If the process is stopped when `Terminate` is called, the process should be continued by using the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method so that the debugger receives confirmation of the termination through the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) or [ICorDebugManagedCallback::ExitAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) callback.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ccced-112">應用程式定義域不實作這個方法。</span><span class="sxs-lookup"><span data-stu-id="ccced-112">This method is not implemented by an application domain.</span></span> <span data-ttu-id="ccced-113">也就是說，它不在實作<xref:System.AppDomain>層級。</span><span class="sxs-lookup"><span data-stu-id="ccced-113">That is, it is not implemented at the <xref:System.AppDomain> level.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccced-114">需求</span><span class="sxs-lookup"><span data-stu-id="ccced-114">Requirements</span></span>  
 <span data-ttu-id="ccced-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ccced-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccced-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ccced-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ccced-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ccced-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ccced-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccced-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccced-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ccced-119">See also</span></span>

