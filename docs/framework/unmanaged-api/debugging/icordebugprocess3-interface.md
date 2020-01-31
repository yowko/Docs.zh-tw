---
title: ICorDebugProcess3 介面
ms.date: 03/30/2017
api_name:
- ICorDebugProcess3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess3
helpviewer_keywords:
- ICorDebugProcess3 interface [.NET Framework debugging]
ms.assetid: ced9c82e-d7b0-4806-a151-98b6611d3097
topic_type:
- apiref
ms.openlocfilehash: 28d1d426276e9654c2122f03fb64735b7e67f44f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792480"
---
# <a name="icordebugprocess3-interface"></a><span data-ttu-id="f61be-102">ICorDebugProcess3 介面</span><span class="sxs-lookup"><span data-stu-id="f61be-102">ICorDebugProcess3 Interface</span></span>
<span data-ttu-id="f61be-103">控制自訂偵錯工具通知。</span><span class="sxs-lookup"><span data-stu-id="f61be-103">Controls custom debugger notifications.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f61be-104">方法</span><span class="sxs-lookup"><span data-stu-id="f61be-104">Methods</span></span>  
  
|<span data-ttu-id="f61be-105">方法</span><span class="sxs-lookup"><span data-stu-id="f61be-105">Method</span></span>|<span data-ttu-id="f61be-106">描述</span><span class="sxs-lookup"><span data-stu-id="f61be-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f61be-107">SetEnableCustomNotification 方法</span><span class="sxs-lookup"><span data-stu-id="f61be-107">SetEnableCustomNotification Method</span></span>](icordebugprocess3-setenablecustomnotification-method.md)|<span data-ttu-id="f61be-108">啟用和停用指定類型的自訂偵錯工具通知。</span><span class="sxs-lookup"><span data-stu-id="f61be-108">Enables and disables custom debugger notifications of the specified type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f61be-109">備註</span><span class="sxs-lookup"><span data-stu-id="f61be-109">Remarks</span></span>  
 <span data-ttu-id="f61be-110">這個介面會以邏輯方式擴充 ICorDebugProcess 和 ICorDebugProcess2 介面。</span><span class="sxs-lookup"><span data-stu-id="f61be-110">This interface logically extends the ICorDebugProcess and ICorDebugProcess2 interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f61be-111">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="f61be-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f61be-112">需求</span><span class="sxs-lookup"><span data-stu-id="f61be-112">Requirements</span></span>  
 <span data-ttu-id="f61be-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f61be-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f61be-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f61be-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f61be-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f61be-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f61be-116">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f61be-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f61be-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="f61be-117">See also</span></span>

- [<span data-ttu-id="f61be-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="f61be-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f61be-119">偵錯</span><span class="sxs-lookup"><span data-stu-id="f61be-119">Debugging</span></span>](index.md)
