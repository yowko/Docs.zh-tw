---
title: ICorDebugDebugEvent::GetThread 方法
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c5b4a15f637526cd2faadd2d9d3da143c40140f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414901"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="12f4f-102">ICorDebugDebugEvent::GetThread 方法</span><span class="sxs-lookup"><span data-stu-id="12f4f-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="12f4f-103">取得發生事件的執行緒。</span><span class="sxs-lookup"><span data-stu-id="12f4f-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12f4f-104">語法</span><span class="sxs-lookup"><span data-stu-id="12f4f-104">Syntax</span></span>  
  
```  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="12f4f-105">參數</span><span class="sxs-lookup"><span data-stu-id="12f4f-105">Parameters</span></span>  
 <span data-ttu-id="12f4f-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="12f4f-106">ppThread</span></span>  
 <span data-ttu-id="12f4f-107">[out]ICorDebugThread 物件，表示的執行緒發生事件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="12f4f-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12f4f-108">備註</span><span class="sxs-lookup"><span data-stu-id="12f4f-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="12f4f-109">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="12f4f-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12f4f-110">需求</span><span class="sxs-lookup"><span data-stu-id="12f4f-110">Requirements</span></span>  
 <span data-ttu-id="12f4f-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="12f4f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12f4f-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="12f4f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12f4f-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12f4f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12f4f-114">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12f4f-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12f4f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12f4f-115">See Also</span></span>  
 [<span data-ttu-id="12f4f-116">ICorDebugDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="12f4f-116">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 [<span data-ttu-id="12f4f-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="12f4f-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
