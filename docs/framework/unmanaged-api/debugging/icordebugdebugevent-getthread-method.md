---
title: ICorDebugDebugEvent::GetThread 方法
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
ms.openlocfilehash: acce18517c105739417fc734b49ff004ca9546dc
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976374"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="6080a-102">ICorDebugDebugEvent::GetThread 方法</span><span class="sxs-lookup"><span data-stu-id="6080a-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="6080a-103">取得發生事件的執行緒。</span><span class="sxs-lookup"><span data-stu-id="6080a-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6080a-104">語法</span><span class="sxs-lookup"><span data-stu-id="6080a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6080a-105">參數</span><span class="sxs-lookup"><span data-stu-id="6080a-105">Parameters</span></span>  
 <span data-ttu-id="6080a-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="6080a-106">ppThread</span></span>  
 <span data-ttu-id="6080a-107">[out] 代表發生事件的執行緒之 ICorDebugThread 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="6080a-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6080a-108">備註</span><span class="sxs-lookup"><span data-stu-id="6080a-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6080a-109">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="6080a-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6080a-110">需求</span><span class="sxs-lookup"><span data-stu-id="6080a-110">Requirements</span></span>  
 <span data-ttu-id="6080a-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6080a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6080a-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6080a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6080a-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6080a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6080a-114">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6080a-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6080a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6080a-115">See also</span></span>

- [<span data-ttu-id="6080a-116">ICorDebugDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="6080a-116">ICorDebugDebugEvent Interface</span></span>](icordebugdebugevent-interface.md)
- [<span data-ttu-id="6080a-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="6080a-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
