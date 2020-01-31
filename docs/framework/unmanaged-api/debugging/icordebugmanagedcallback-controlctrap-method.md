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
ms.openlocfilehash: 63f7bf8c09480b9ce2cfb8eb8dc66e4a6133ef8f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777478"
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a><span data-ttu-id="f2f88-102">ICorDebugManagedCallback::ControlCTrap 方法</span><span class="sxs-lookup"><span data-stu-id="f2f88-102">ICorDebugManagedCallback::ControlCTrap Method</span></span>
<span data-ttu-id="f2f88-103">通知偵錯工具在正在進行調試的進程中，已攔截 CTRL + C。</span><span class="sxs-lookup"><span data-stu-id="f2f88-103">Notifies the debugger that a CTRL+C is trapped in the process that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2f88-104">語法</span><span class="sxs-lookup"><span data-stu-id="f2f88-104">Syntax</span></span>  
  
```cpp  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2f88-105">參數</span><span class="sxs-lookup"><span data-stu-id="f2f88-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="f2f88-106">在ICorDebugProcess 物件的指標，代表用來攔截 CTRL + C 的進程。</span><span class="sxs-lookup"><span data-stu-id="f2f88-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the CTRL+C is trapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f2f88-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="f2f88-107">Return Value</span></span>  
  
|<span data-ttu-id="f2f88-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f2f88-108">HRESULT</span></span>|<span data-ttu-id="f2f88-109">描述</span><span class="sxs-lookup"><span data-stu-id="f2f88-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f2f88-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f2f88-110">S_OK</span></span>|<span data-ttu-id="f2f88-111">偵錯工具將會處理 CTRL + C 陷阱。</span><span class="sxs-lookup"><span data-stu-id="f2f88-111">The debugger will handle the CTRL+C trap.</span></span>|  
|<span data-ttu-id="f2f88-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="f2f88-112">S_FALSE</span></span>|<span data-ttu-id="f2f88-113">偵錯工具將不會處理 CTRL + C 陷阱。</span><span class="sxs-lookup"><span data-stu-id="f2f88-113">The debugger will not handle the CTRL+C trap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2f88-114">備註</span><span class="sxs-lookup"><span data-stu-id="f2f88-114">Remarks</span></span>  
 <span data-ttu-id="f2f88-115">此回呼的進程中的所有應用程式域都會停止。</span><span class="sxs-lookup"><span data-stu-id="f2f88-115">All application domains within the process are stopped for this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2f88-116">需求</span><span class="sxs-lookup"><span data-stu-id="f2f88-116">Requirements</span></span>  
 <span data-ttu-id="f2f88-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f2f88-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2f88-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2f88-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2f88-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2f88-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2f88-120">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2f88-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2f88-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="f2f88-121">See also</span></span>

- [<span data-ttu-id="f2f88-122">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="f2f88-122">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
