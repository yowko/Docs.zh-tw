---
title: "ICorDebugDebugEvent::GetThread 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 13b950545c2c8c8b54d24b932351d80280e1dac0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="27791-102">ICorDebugDebugEvent::GetThread 方法</span><span class="sxs-lookup"><span data-stu-id="27791-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="27791-103">取得發生事件的執行緒。</span><span class="sxs-lookup"><span data-stu-id="27791-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27791-104">語法</span><span class="sxs-lookup"><span data-stu-id="27791-104">Syntax</span></span>  
  
```  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="27791-105">參數</span><span class="sxs-lookup"><span data-stu-id="27791-105">Parameters</span></span>  
 <span data-ttu-id="27791-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="27791-106">ppThread</span></span>  
 <span data-ttu-id="27791-107">[out]ICorDebugThread 物件，表示的執行緒發生事件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="27791-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27791-108">備註</span><span class="sxs-lookup"><span data-stu-id="27791-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="27791-109">這個方法僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="27791-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27791-110">需求</span><span class="sxs-lookup"><span data-stu-id="27791-110">Requirements</span></span>  
 <span data-ttu-id="27791-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="27791-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27791-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="27791-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="27791-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27791-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27791-114">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27791-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27791-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27791-115">See Also</span></span>  
 [<span data-ttu-id="27791-116">ICorDebugDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="27791-116">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 [<span data-ttu-id="27791-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="27791-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
