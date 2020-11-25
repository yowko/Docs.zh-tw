---
title: ICorDebugManagedCallback::Exception 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Exception
helpviewer_keywords:
- Exception method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::Exception method [.NET Framework debugging]
ms.assetid: ab18a509-dff3-4930-b585-bd15e0414176
topic_type:
- apiref
ms.openlocfilehash: 05fed13a556cbcc3b8362e41d73c2b659b1e5eeb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731783"
---
# <a name="icordebugmanagedcallbackexception-method"></a><span data-ttu-id="74353-102">ICorDebugManagedCallback::Exception 方法</span><span class="sxs-lookup"><span data-stu-id="74353-102">ICorDebugManagedCallback::Exception Method</span></span>

<span data-ttu-id="74353-103">通知偵錯工具已從 managed 程式碼擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="74353-103">Notifies the debugger that an exception has been thrown from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74353-104">語法</span><span class="sxs-lookup"><span data-stu-id="74353-104">Syntax</span></span>  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74353-105">參數</span><span class="sxs-lookup"><span data-stu-id="74353-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="74353-106">在ICorDebugAppDomain 物件的指標，代表擲回例外狀況的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="74353-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="74353-107">在代表擲回例外狀況之執行緒的 ICorDebugThread 物件指標。</span><span class="sxs-lookup"><span data-stu-id="74353-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the exception was thrown.</span></span>  
  
 `unhandled`  
 <span data-ttu-id="74353-108">在如果這個值為 `false` ，則應用程式尚未處理例外狀況，否則例外狀況會被未處理，並會終止進程。</span><span class="sxs-lookup"><span data-stu-id="74353-108">[in] If this value is `false`, the exception has not yet been processed by the application; otherwise, the exception is unhandled and will terminate the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74353-109">備註</span><span class="sxs-lookup"><span data-stu-id="74353-109">Remarks</span></span>  

 <span data-ttu-id="74353-110">您可以從執行緒物件中取出特定的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="74353-110">The specific exception can be retrieved from the thread object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74353-111">需求</span><span class="sxs-lookup"><span data-stu-id="74353-111">Requirements</span></span>  

 <span data-ttu-id="74353-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="74353-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74353-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="74353-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74353-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74353-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74353-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74353-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74353-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74353-116">See also</span></span>

- [<span data-ttu-id="74353-117">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="74353-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
