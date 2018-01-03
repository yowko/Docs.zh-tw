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
ms.workload: dotnet
ms.openlocfilehash: faf1ace6c65f38e9a1d5b958b633c95dbcd3dcf8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="51277-102">ICorDebugDebugEvent::GetThread 方法</span><span class="sxs-lookup"><span data-stu-id="51277-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="51277-103">取得發生事件的執行緒。</span><span class="sxs-lookup"><span data-stu-id="51277-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51277-104">語法</span><span class="sxs-lookup"><span data-stu-id="51277-104">Syntax</span></span>  
  
```  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="51277-105">參數</span><span class="sxs-lookup"><span data-stu-id="51277-105">Parameters</span></span>  
 <span data-ttu-id="51277-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="51277-106">ppThread</span></span>  
 <span data-ttu-id="51277-107">[out]ICorDebugThread 物件，表示的執行緒發生事件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="51277-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51277-108">備註</span><span class="sxs-lookup"><span data-stu-id="51277-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51277-109">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="51277-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51277-110">需求</span><span class="sxs-lookup"><span data-stu-id="51277-110">Requirements</span></span>  
 <span data-ttu-id="51277-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="51277-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51277-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51277-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51277-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51277-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51277-114">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51277-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51277-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="51277-115">See Also</span></span>  
 [<span data-ttu-id="51277-116">ICorDebugDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="51277-116">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 [<span data-ttu-id="51277-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="51277-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
