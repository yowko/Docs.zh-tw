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
ms.openlocfilehash: eade3fd5d946c44ae4a77c571f762709de3cef40
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976560"
---
# <a name="icordebugcontrollerterminate-method"></a><span data-ttu-id="0c03d-102">ICorDebugController::Terminate 方法</span><span class="sxs-lookup"><span data-stu-id="0c03d-102">ICorDebugController::Terminate Method</span></span>
<span data-ttu-id="0c03d-103">使用指定的結束代碼終止進程。</span><span class="sxs-lookup"><span data-stu-id="0c03d-103">Terminates the process with the specified exit code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0c03d-104">這個方法是 Win32 `TerminateProcess`函數的包裝函式。</span><span class="sxs-lookup"><span data-stu-id="0c03d-104">This method is a wrapper for the Win32 `TerminateProcess` function.</span></span> <span data-ttu-id="0c03d-105">因此， `Terminate`會以 Win32 `TerminateProcess`函數使用結束代碼的相同方式來使用它。</span><span class="sxs-lookup"><span data-stu-id="0c03d-105">Thus, `Terminate` uses the exit code in the same way that the Win32 `TerminateProcess` function uses it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c03d-106">語法</span><span class="sxs-lookup"><span data-stu-id="0c03d-106">Syntax</span></span>  
  
```cpp  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c03d-107">參數</span><span class="sxs-lookup"><span data-stu-id="0c03d-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="0c03d-108">在表示結束代碼的數值。</span><span class="sxs-lookup"><span data-stu-id="0c03d-108">[in] A numeric value that is the exit code.</span></span> <span data-ttu-id="0c03d-109">有效的數值定義于 Winbase 中。</span><span class="sxs-lookup"><span data-stu-id="0c03d-109">The valid numeric values are defined in Winbase.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c03d-110">備註</span><span class="sxs-lookup"><span data-stu-id="0c03d-110">Remarks</span></span>  
 <span data-ttu-id="0c03d-111">`Terminate`如果呼叫時停止進程，則應該使用[ICorDebugController：： Continue](icordebugcontroller-continue-method.md)方法繼續處理，讓偵錯工具透過[ICorDebugManagedCallback：： ExitProcess](icordebugmanagedcallback-exitprocess-method.md)或[ICorDebugManagedCallback：： ExitAppDomain](icordebugmanagedcallback-exitappdomain-method.md)回呼接收終止的確認。</span><span class="sxs-lookup"><span data-stu-id="0c03d-111">If the process is stopped when `Terminate` is called, the process should be continued by using the [ICorDebugController::Continue](icordebugcontroller-continue-method.md) method so that the debugger receives confirmation of the termination through the [ICorDebugManagedCallback::ExitProcess](icordebugmanagedcallback-exitprocess-method.md) or [ICorDebugManagedCallback::ExitAppDomain](icordebugmanagedcallback-exitappdomain-method.md) callback.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0c03d-112">這個方法不是由應用程式域所執行。</span><span class="sxs-lookup"><span data-stu-id="0c03d-112">This method is not implemented by an application domain.</span></span> <span data-ttu-id="0c03d-113">也就是說，它不會在<xref:System.AppDomain>層級上執行。</span><span class="sxs-lookup"><span data-stu-id="0c03d-113">That is, it is not implemented at the <xref:System.AppDomain> level.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c03d-114">需求</span><span class="sxs-lookup"><span data-stu-id="0c03d-114">Requirements</span></span>  
 <span data-ttu-id="0c03d-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0c03d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c03d-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0c03d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c03d-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c03d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c03d-118">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c03d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c03d-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c03d-119">See also</span></span>
