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
ms.openlocfilehash: 33a68d11a8d17e46533b4f83bbf87aafe171e612
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212395"
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a><span data-ttu-id="04b8a-102">ICorDebugManagedCallback::ControlCTrap 方法</span><span class="sxs-lookup"><span data-stu-id="04b8a-102">ICorDebugManagedCallback::ControlCTrap Method</span></span>
<span data-ttu-id="04b8a-103">通知偵錯工具在正在進行調試的進程中，已攔截 CTRL + C。</span><span class="sxs-lookup"><span data-stu-id="04b8a-103">Notifies the debugger that a CTRL+C is trapped in the process that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04b8a-104">語法</span><span class="sxs-lookup"><span data-stu-id="04b8a-104">Syntax</span></span>  
  
```cpp  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04b8a-105">參數</span><span class="sxs-lookup"><span data-stu-id="04b8a-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="04b8a-106">在ICorDebugProcess 物件的指標，代表用來攔截 CTRL + C 的進程。</span><span class="sxs-lookup"><span data-stu-id="04b8a-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the CTRL+C is trapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04b8a-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="04b8a-107">Return Value</span></span>  
  
|<span data-ttu-id="04b8a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="04b8a-108">HRESULT</span></span>|<span data-ttu-id="04b8a-109">描述</span><span class="sxs-lookup"><span data-stu-id="04b8a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="04b8a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="04b8a-110">S_OK</span></span>|<span data-ttu-id="04b8a-111">偵錯工具將會處理 CTRL + C 陷阱。</span><span class="sxs-lookup"><span data-stu-id="04b8a-111">The debugger will handle the CTRL+C trap.</span></span>|  
|<span data-ttu-id="04b8a-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="04b8a-112">S_FALSE</span></span>|<span data-ttu-id="04b8a-113">偵錯工具將不會處理 CTRL + C 陷阱。</span><span class="sxs-lookup"><span data-stu-id="04b8a-113">The debugger will not handle the CTRL+C trap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04b8a-114">備註</span><span class="sxs-lookup"><span data-stu-id="04b8a-114">Remarks</span></span>  
 <span data-ttu-id="04b8a-115">此回呼的進程中的所有應用程式域都會停止。</span><span class="sxs-lookup"><span data-stu-id="04b8a-115">All application domains within the process are stopped for this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04b8a-116">需求</span><span class="sxs-lookup"><span data-stu-id="04b8a-116">Requirements</span></span>  
 <span data-ttu-id="04b8a-117">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="04b8a-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04b8a-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="04b8a-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04b8a-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04b8a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04b8a-120">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04b8a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04b8a-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="04b8a-121">See also</span></span>

- [<span data-ttu-id="04b8a-122">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="04b8a-122">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
