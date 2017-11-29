---
title: "ICorDebugManagedCallback::ControlCTrap 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.ControlCTrap
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::ControlCTrap
helpviewer_keywords:
- ICorDebugManagedCallback::ControlCTrap method [.NET Framework debugging]
- ControlCTrap method [.NET Framework debugging]
ms.assetid: 0500854e-2121-43d9-a028-64312da35258
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: df6aab0f8f220e53c8aab0d40a8b300d95822068
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a><span data-ttu-id="4fd95-102">ICorDebugManagedCallback::ControlCTrap 方法</span><span class="sxs-lookup"><span data-stu-id="4fd95-102">ICorDebugManagedCallback::ControlCTrap Method</span></span>
<span data-ttu-id="4fd95-103">CTRL + C 陷入正在偵錯的處理程序會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="4fd95-103">Notifies the debugger that a CTRL+C is trapped in the process that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fd95-104">語法</span><span class="sxs-lookup"><span data-stu-id="4fd95-104">Syntax</span></span>  
  
```  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4fd95-105">參數</span><span class="sxs-lookup"><span data-stu-id="4fd95-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="4fd95-106">[in]代表程序的 CTRL + C 會被截取 ICorDebugProcess 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="4fd95-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the CTRL+C is trapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4fd95-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="4fd95-107">Return Value</span></span>  
  
|<span data-ttu-id="4fd95-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4fd95-108">HRESULT</span></span>|<span data-ttu-id="4fd95-109">描述</span><span class="sxs-lookup"><span data-stu-id="4fd95-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4fd95-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4fd95-110">S_OK</span></span>|<span data-ttu-id="4fd95-111">偵錯工具就會處理 CTRL + C 設陷。</span><span class="sxs-lookup"><span data-stu-id="4fd95-111">The debugger will handle the CTRL+C trap.</span></span>|  
|<span data-ttu-id="4fd95-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="4fd95-112">S_FALSE</span></span>|<span data-ttu-id="4fd95-113">偵錯工具不會處理 CTRL + C 設陷。</span><span class="sxs-lookup"><span data-stu-id="4fd95-113">The debugger will not handle the CTRL+C trap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4fd95-114">備註</span><span class="sxs-lookup"><span data-stu-id="4fd95-114">Remarks</span></span>  
 <span data-ttu-id="4fd95-115">處理序內的所有應用程式定義域會停止這個回呼。</span><span class="sxs-lookup"><span data-stu-id="4fd95-115">All application domains within the process are stopped for this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fd95-116">需求</span><span class="sxs-lookup"><span data-stu-id="4fd95-116">Requirements</span></span>  
 <span data-ttu-id="4fd95-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4fd95-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fd95-118">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4fd95-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4fd95-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4fd95-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4fd95-120">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fd95-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fd95-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fd95-121">See Also</span></span>  
 [<span data-ttu-id="4fd95-122">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="4fd95-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
