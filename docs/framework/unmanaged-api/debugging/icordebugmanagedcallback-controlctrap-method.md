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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd84293b3414a8622c6b91717e9f1b2f2ce85286
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472469"
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a><span data-ttu-id="bed0c-102">ICorDebugManagedCallback::ControlCTrap 方法</span><span class="sxs-lookup"><span data-stu-id="bed0c-102">ICorDebugManagedCallback::ControlCTrap Method</span></span>
<span data-ttu-id="bed0c-103">CTRL + C 會陷入正在偵錯的處理程序會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="bed0c-103">Notifies the debugger that a CTRL+C is trapped in the process that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bed0c-104">語法</span><span class="sxs-lookup"><span data-stu-id="bed0c-104">Syntax</span></span>  
  
```  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bed0c-105">參數</span><span class="sxs-lookup"><span data-stu-id="bed0c-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="bed0c-106">[in]表示處理程序的 CTRL + C 會被截取的 ICorDebugProcess 物件指標。</span><span class="sxs-lookup"><span data-stu-id="bed0c-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the CTRL+C is trapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bed0c-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="bed0c-107">Return Value</span></span>  
  
|<span data-ttu-id="bed0c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bed0c-108">HRESULT</span></span>|<span data-ttu-id="bed0c-109">描述</span><span class="sxs-lookup"><span data-stu-id="bed0c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bed0c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bed0c-110">S_OK</span></span>|<span data-ttu-id="bed0c-111">偵錯工具會處理 CTRL + C 設陷。</span><span class="sxs-lookup"><span data-stu-id="bed0c-111">The debugger will handle the CTRL+C trap.</span></span>|  
|<span data-ttu-id="bed0c-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="bed0c-112">S_FALSE</span></span>|<span data-ttu-id="bed0c-113">偵錯工具不會處理 CTRL + C 設陷。</span><span class="sxs-lookup"><span data-stu-id="bed0c-113">The debugger will not handle the CTRL+C trap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bed0c-114">備註</span><span class="sxs-lookup"><span data-stu-id="bed0c-114">Remarks</span></span>  
 <span data-ttu-id="bed0c-115">在程序中的所有應用程式定義域會停止這個回呼。</span><span class="sxs-lookup"><span data-stu-id="bed0c-115">All application domains within the process are stopped for this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bed0c-116">需求</span><span class="sxs-lookup"><span data-stu-id="bed0c-116">Requirements</span></span>  
 <span data-ttu-id="bed0c-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bed0c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bed0c-118">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bed0c-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bed0c-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bed0c-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bed0c-120">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bed0c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bed0c-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bed0c-121">See also</span></span>
- [<span data-ttu-id="bed0c-122">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="bed0c-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
