---
title: ICorDebugDebugEvent::GetThread 方法
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
ms.openlocfilehash: 0900ac2ae5bcf2141e720dad6efdf68d4fafaccc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793527"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="59cd5-102">ICorDebugDebugEvent::GetThread 方法</span><span class="sxs-lookup"><span data-stu-id="59cd5-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="59cd5-103">取得發生事件的執行緒。</span><span class="sxs-lookup"><span data-stu-id="59cd5-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59cd5-104">語法</span><span class="sxs-lookup"><span data-stu-id="59cd5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59cd5-105">參數</span><span class="sxs-lookup"><span data-stu-id="59cd5-105">Parameters</span></span>  
 <span data-ttu-id="59cd5-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="59cd5-106">ppThread</span></span>  
 <span data-ttu-id="59cd5-107">[out] 代表發生事件的執行緒之 ICorDebugThread 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="59cd5-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59cd5-108">備註</span><span class="sxs-lookup"><span data-stu-id="59cd5-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="59cd5-109">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="59cd5-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59cd5-110">需求</span><span class="sxs-lookup"><span data-stu-id="59cd5-110">Requirements</span></span>  
 <span data-ttu-id="59cd5-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="59cd5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59cd5-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="59cd5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59cd5-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59cd5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59cd5-114">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59cd5-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59cd5-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="59cd5-115">See also</span></span>

- [<span data-ttu-id="59cd5-116">ICorDebugDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="59cd5-116">ICorDebugDebugEvent Interface</span></span>](icordebugdebugevent-interface.md)
- [<span data-ttu-id="59cd5-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="59cd5-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
