---
title: ICorDebugManagedCallback::ControlCTrap 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ControlCTrap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ControlCTrap
helpviewer_keywords:
- ICorDebugManagedCallback::ControlCTrap method [.NET Framework debugging]
- ControlCTrap method [.NET Framework debugging]
ms.assetid: 0500854e-2121-43d9-a028-64312da35258
topic_type:
- apiref
ms.openlocfilehash: da35db8a943fda5fb3fbf4126684bb9cb7243001
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137419"
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a><span data-ttu-id="8091f-102">ICorDebugManagedCallback::ControlCTrap 方法</span><span class="sxs-lookup"><span data-stu-id="8091f-102">ICorDebugManagedCallback::ControlCTrap Method</span></span>
<span data-ttu-id="8091f-103">通知偵錯工具在正在進行調試的進程中，已攔截 CTRL + C。</span><span class="sxs-lookup"><span data-stu-id="8091f-103">Notifies the debugger that a CTRL+C is trapped in the process that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8091f-104">語法</span><span class="sxs-lookup"><span data-stu-id="8091f-104">Syntax</span></span>  
  
```cpp  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8091f-105">參數</span><span class="sxs-lookup"><span data-stu-id="8091f-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="8091f-106">在ICorDebugProcess 物件的指標，代表用來攔截 CTRL + C 的進程。</span><span class="sxs-lookup"><span data-stu-id="8091f-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the CTRL+C is trapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8091f-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="8091f-107">Return Value</span></span>  
  
|<span data-ttu-id="8091f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8091f-108">HRESULT</span></span>|<span data-ttu-id="8091f-109">描述</span><span class="sxs-lookup"><span data-stu-id="8091f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8091f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8091f-110">S_OK</span></span>|<span data-ttu-id="8091f-111">偵錯工具將會處理 CTRL + C 陷阱。</span><span class="sxs-lookup"><span data-stu-id="8091f-111">The debugger will handle the CTRL+C trap.</span></span>|  
|<span data-ttu-id="8091f-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="8091f-112">S_FALSE</span></span>|<span data-ttu-id="8091f-113">偵錯工具將不會處理 CTRL + C 陷阱。</span><span class="sxs-lookup"><span data-stu-id="8091f-113">The debugger will not handle the CTRL+C trap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8091f-114">備註</span><span class="sxs-lookup"><span data-stu-id="8091f-114">Remarks</span></span>  
 <span data-ttu-id="8091f-115">此回呼的進程中的所有應用程式域都會停止。</span><span class="sxs-lookup"><span data-stu-id="8091f-115">All application domains within the process are stopped for this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8091f-116">需求</span><span class="sxs-lookup"><span data-stu-id="8091f-116">Requirements</span></span>  
 <span data-ttu-id="8091f-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8091f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8091f-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8091f-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8091f-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8091f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8091f-120">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8091f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8091f-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="8091f-121">See also</span></span>

- [<span data-ttu-id="8091f-122">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="8091f-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
