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
ms.openlocfilehash: 0c38269ea4d730d8f3f9ba5d2c5d8f0edf6d7d45
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731829"
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a><span data-ttu-id="498ba-102">ICorDebugManagedCallback::ControlCTrap 方法</span><span class="sxs-lookup"><span data-stu-id="498ba-102">ICorDebugManagedCallback::ControlCTrap Method</span></span>

<span data-ttu-id="498ba-103">通知偵錯工具，在正在進行調試的進程中攔截 CTRL + C。</span><span class="sxs-lookup"><span data-stu-id="498ba-103">Notifies the debugger that a CTRL+C is trapped in the process that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="498ba-104">語法</span><span class="sxs-lookup"><span data-stu-id="498ba-104">Syntax</span></span>  
  
```cpp  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="498ba-105">參數</span><span class="sxs-lookup"><span data-stu-id="498ba-105">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="498ba-106">在ICorDebugProcess 物件的指標，該物件代表用來捕捉 CTRL + C 的進程。</span><span class="sxs-lookup"><span data-stu-id="498ba-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the CTRL+C is trapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="498ba-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="498ba-107">Return Value</span></span>  
  
|<span data-ttu-id="498ba-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="498ba-108">HRESULT</span></span>|<span data-ttu-id="498ba-109">描述</span><span class="sxs-lookup"><span data-stu-id="498ba-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="498ba-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="498ba-110">S_OK</span></span>|<span data-ttu-id="498ba-111">偵錯工具將會處理 CTRL + C 陷阱。</span><span class="sxs-lookup"><span data-stu-id="498ba-111">The debugger will handle the CTRL+C trap.</span></span>|  
|<span data-ttu-id="498ba-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="498ba-112">S_FALSE</span></span>|<span data-ttu-id="498ba-113">偵錯工具不會處理 CTRL + C 陷阱。</span><span class="sxs-lookup"><span data-stu-id="498ba-113">The debugger will not handle the CTRL+C trap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="498ba-114">備註</span><span class="sxs-lookup"><span data-stu-id="498ba-114">Remarks</span></span>  

 <span data-ttu-id="498ba-115">此回呼的進程中的所有應用程式域都已停止。</span><span class="sxs-lookup"><span data-stu-id="498ba-115">All application domains within the process are stopped for this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="498ba-116">需求</span><span class="sxs-lookup"><span data-stu-id="498ba-116">Requirements</span></span>  

 <span data-ttu-id="498ba-117">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="498ba-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="498ba-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="498ba-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="498ba-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="498ba-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="498ba-120">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="498ba-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="498ba-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="498ba-121">See also</span></span>

- [<span data-ttu-id="498ba-122">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="498ba-122">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
