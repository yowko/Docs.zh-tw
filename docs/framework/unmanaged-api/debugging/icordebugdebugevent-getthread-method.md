---
title: ICorDebugDebugEvent::GetThread 方法
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51d674159b33cad1a77a82e39b9f11a38c98cbd3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687397"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="4048e-102">ICorDebugDebugEvent::GetThread 方法</span><span class="sxs-lookup"><span data-stu-id="4048e-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="4048e-103">取得發生事件的執行緒。</span><span class="sxs-lookup"><span data-stu-id="4048e-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4048e-104">語法</span><span class="sxs-lookup"><span data-stu-id="4048e-104">Syntax</span></span>  
  
```  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4048e-105">參數</span><span class="sxs-lookup"><span data-stu-id="4048e-105">Parameters</span></span>  
 <span data-ttu-id="4048e-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="4048e-106">ppThread</span></span>  
 <span data-ttu-id="4048e-107">[out]ICorDebugThread 物件，表示發生事件之執行緒的位址指標。</span><span class="sxs-lookup"><span data-stu-id="4048e-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4048e-108">備註</span><span class="sxs-lookup"><span data-stu-id="4048e-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4048e-109">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="4048e-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4048e-110">需求</span><span class="sxs-lookup"><span data-stu-id="4048e-110">Requirements</span></span>  
 <span data-ttu-id="4048e-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4048e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4048e-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4048e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4048e-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4048e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4048e-114">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4048e-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4048e-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4048e-115">See also</span></span>
- [<span data-ttu-id="4048e-116">ICorDebugDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="4048e-116">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [<span data-ttu-id="4048e-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="4048e-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
