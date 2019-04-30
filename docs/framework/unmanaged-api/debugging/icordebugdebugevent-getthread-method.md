---
title: ICorDebugDebugEvent::GetThread 方法
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 103768918f67ca695a47c52b9cd97f24fb8d46ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996121"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="0c6a9-102">ICorDebugDebugEvent::GetThread 方法</span><span class="sxs-lookup"><span data-stu-id="0c6a9-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="0c6a9-103">取得發生事件的執行緒。</span><span class="sxs-lookup"><span data-stu-id="0c6a9-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c6a9-104">語法</span><span class="sxs-lookup"><span data-stu-id="0c6a9-104">Syntax</span></span>  
  
```  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c6a9-105">參數</span><span class="sxs-lookup"><span data-stu-id="0c6a9-105">Parameters</span></span>  
 <span data-ttu-id="0c6a9-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="0c6a9-106">ppThread</span></span>  
 <span data-ttu-id="0c6a9-107">[out]ICorDebugThread 物件，表示發生事件之執行緒的位址指標。</span><span class="sxs-lookup"><span data-stu-id="0c6a9-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c6a9-108">備註</span><span class="sxs-lookup"><span data-stu-id="0c6a9-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c6a9-109">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="0c6a9-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c6a9-110">需求</span><span class="sxs-lookup"><span data-stu-id="0c6a9-110">Requirements</span></span>  
 <span data-ttu-id="0c6a9-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0c6a9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c6a9-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0c6a9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c6a9-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c6a9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c6a9-114">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c6a9-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c6a9-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c6a9-115">See also</span></span>

- [<span data-ttu-id="0c6a9-116">ICorDebugDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="0c6a9-116">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [<span data-ttu-id="0c6a9-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="0c6a9-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
