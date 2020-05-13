---
title: ICorDebugManagedCallback::CreateThread 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateThread method
helpviewer_keywords:
- ICorDebugManagedCallback::CreateThread method [.NET Framework debugging]
- CreateThread method [.NET Framework debugging]
ms.assetid: 6b961728-21c4-4e8d-ae81-197458be62f4
topic_type:
- apiref
ms.openlocfilehash: 5fa3bafd35912a7729833896f7e6f0bb2ff9b121
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212382"
---
# <a name="icordebugmanagedcallbackcreatethread-method"></a><span data-ttu-id="d23e0-102">ICorDebugManagedCallback::CreateThread 方法</span><span class="sxs-lookup"><span data-stu-id="d23e0-102">ICorDebugManagedCallback::CreateThread Method</span></span>
<span data-ttu-id="d23e0-103">通知偵錯工具執行緒已開始執行 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="d23e0-103">Notifies the debugger that a thread has started executing managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d23e0-104">語法</span><span class="sxs-lookup"><span data-stu-id="d23e0-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d23e0-105">參數</span><span class="sxs-lookup"><span data-stu-id="d23e0-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="d23e0-106">在ICorDebugAppDomain 物件的指標，表示包含執行緒的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="d23e0-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="d23e0-107">在代表執行緒之 ICorDebugThread 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="d23e0-107">[in] A pointer to an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d23e0-108">備註</span><span class="sxs-lookup"><span data-stu-id="d23e0-108">Remarks</span></span>  
 <span data-ttu-id="d23e0-109">執行緒將定位於要執行的第一個 managed 程式碼指令。</span><span class="sxs-lookup"><span data-stu-id="d23e0-109">The thread will be positioned at the first managed code instruction to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d23e0-110">需求</span><span class="sxs-lookup"><span data-stu-id="d23e0-110">Requirements</span></span>  
 <span data-ttu-id="d23e0-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d23e0-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d23e0-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d23e0-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d23e0-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d23e0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d23e0-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d23e0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d23e0-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="d23e0-115">See also</span></span>

- [<span data-ttu-id="d23e0-116">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="d23e0-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
