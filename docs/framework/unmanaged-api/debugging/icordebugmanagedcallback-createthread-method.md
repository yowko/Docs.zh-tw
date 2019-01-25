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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd48fae74665f079100b128990656f3a6d002d43
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54586523"
---
# <a name="icordebugmanagedcallbackcreatethread-method"></a><span data-ttu-id="4df42-102">ICorDebugManagedCallback::CreateThread 方法</span><span class="sxs-lookup"><span data-stu-id="4df42-102">ICorDebugManagedCallback::CreateThread Method</span></span>
<span data-ttu-id="4df42-103">執行緒已開始執行 managed 程式碼會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="4df42-103">Notifies the debugger that a thread has started executing managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4df42-104">語法</span><span class="sxs-lookup"><span data-stu-id="4df42-104">Syntax</span></span>  
  
```  
HRESULT CreateThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4df42-105">參數</span><span class="sxs-lookup"><span data-stu-id="4df42-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="4df42-106">[in]表示包含執行緒的應用程式定義域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="4df42-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="4df42-107">[in]ICorDebugThread 物件，表示執行緒指標。</span><span class="sxs-lookup"><span data-stu-id="4df42-107">[in] A pointer to an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4df42-108">備註</span><span class="sxs-lookup"><span data-stu-id="4df42-108">Remarks</span></span>  
 <span data-ttu-id="4df42-109">執行緒會位於第一個要執行的 managed 程式碼指令。</span><span class="sxs-lookup"><span data-stu-id="4df42-109">The thread will be positioned at the first managed code instruction to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4df42-110">需求</span><span class="sxs-lookup"><span data-stu-id="4df42-110">Requirements</span></span>  
 <span data-ttu-id="4df42-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4df42-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4df42-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4df42-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4df42-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4df42-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4df42-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4df42-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4df42-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4df42-115">See also</span></span>
- [<span data-ttu-id="4df42-116">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="4df42-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
