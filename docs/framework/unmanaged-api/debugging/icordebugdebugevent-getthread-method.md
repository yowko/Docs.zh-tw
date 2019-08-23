---
title: ICorDebugDebugEvent::GetThread 方法
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4f85dccd5b59610c52adcf685828984c9344fd49
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911288"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="3077c-102">ICorDebugDebugEvent::GetThread 方法</span><span class="sxs-lookup"><span data-stu-id="3077c-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="3077c-103">取得發生事件的執行緒。</span><span class="sxs-lookup"><span data-stu-id="3077c-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3077c-104">語法</span><span class="sxs-lookup"><span data-stu-id="3077c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3077c-105">參數</span><span class="sxs-lookup"><span data-stu-id="3077c-105">Parameters</span></span>  
 <span data-ttu-id="3077c-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="3077c-106">ppThread</span></span>  
 <span data-ttu-id="3077c-107">脫銷ICorDebugThread 物件位址的指標, 表示發生事件的執行緒。</span><span class="sxs-lookup"><span data-stu-id="3077c-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3077c-108">備註</span><span class="sxs-lookup"><span data-stu-id="3077c-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3077c-109">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="3077c-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3077c-110">需求</span><span class="sxs-lookup"><span data-stu-id="3077c-110">Requirements</span></span>  
 <span data-ttu-id="3077c-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3077c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3077c-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3077c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3077c-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3077c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3077c-114">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3077c-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3077c-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3077c-115">See also</span></span>

- [<span data-ttu-id="3077c-116">ICorDebugDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="3077c-116">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [<span data-ttu-id="3077c-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="3077c-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
