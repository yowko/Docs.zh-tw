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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95c2218aadd62902ff9bc7f2e6a190aa2ce241ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418843"
---
# <a name="icordebugprocess3-interface"></a><span data-ttu-id="a2153-102">ICorDebugProcess3 介面</span><span class="sxs-lookup"><span data-stu-id="a2153-102">ICorDebugProcess3 Interface</span></span>
<span data-ttu-id="a2153-103">控制自訂偵錯工具通知。</span><span class="sxs-lookup"><span data-stu-id="a2153-103">Controls custom debugger notifications.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a2153-104">方法</span><span class="sxs-lookup"><span data-stu-id="a2153-104">Methods</span></span>  
  
|<span data-ttu-id="a2153-105">方法</span><span class="sxs-lookup"><span data-stu-id="a2153-105">Method</span></span>|<span data-ttu-id="a2153-106">描述</span><span class="sxs-lookup"><span data-stu-id="a2153-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a2153-107">SetEnableCustomNotification 方法</span><span class="sxs-lookup"><span data-stu-id="a2153-107">SetEnableCustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md)|<span data-ttu-id="a2153-108">啟用和停用指定之類型的自訂偵錯工具通知。</span><span class="sxs-lookup"><span data-stu-id="a2153-108">Enables and disables custom debugger notifications of the specified type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2153-109">備註</span><span class="sxs-lookup"><span data-stu-id="a2153-109">Remarks</span></span>  
 <span data-ttu-id="a2153-110">這個介面會以邏輯方式擴充的 ICorDebugProcess 和 ICorDebugProcess2 介面。</span><span class="sxs-lookup"><span data-stu-id="a2153-110">This interface logically extends the ICorDebugProcess and ICorDebugProcess2 interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a2153-111">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="a2153-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2153-112">需求</span><span class="sxs-lookup"><span data-stu-id="a2153-112">Requirements</span></span>  
 <span data-ttu-id="a2153-113">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a2153-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2153-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2153-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2153-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2153-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2153-116">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2153-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2153-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2153-117">See Also</span></span>  
 [<span data-ttu-id="a2153-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a2153-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="a2153-119">偵錯</span><span class="sxs-lookup"><span data-stu-id="a2153-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
