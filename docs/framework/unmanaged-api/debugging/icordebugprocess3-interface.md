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
ms.openlocfilehash: 0ccc45482f691d9950c641ef126a657052a280e8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213630"
---
# <a name="icordebugprocess3-interface"></a><span data-ttu-id="a3b70-102">ICorDebugProcess3 介面</span><span class="sxs-lookup"><span data-stu-id="a3b70-102">ICorDebugProcess3 Interface</span></span>
<span data-ttu-id="a3b70-103">控制自訂偵錯工具通知。</span><span class="sxs-lookup"><span data-stu-id="a3b70-103">Controls custom debugger notifications.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a3b70-104">方法</span><span class="sxs-lookup"><span data-stu-id="a3b70-104">Methods</span></span>  
  
|<span data-ttu-id="a3b70-105">方法</span><span class="sxs-lookup"><span data-stu-id="a3b70-105">Method</span></span>|<span data-ttu-id="a3b70-106">描述</span><span class="sxs-lookup"><span data-stu-id="a3b70-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a3b70-107">SetEnableCustomNotification 方法</span><span class="sxs-lookup"><span data-stu-id="a3b70-107">SetEnableCustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md)|<span data-ttu-id="a3b70-108">啟用和停用指定之型別的自訂偵錯工具通知。</span><span class="sxs-lookup"><span data-stu-id="a3b70-108">Enables and disables custom debugger notifications of the specified type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3b70-109">備註</span><span class="sxs-lookup"><span data-stu-id="a3b70-109">Remarks</span></span>  
 <span data-ttu-id="a3b70-110">這個介面會以邏輯方式擴充 ICorDebugProcess 和 ICorDebugProcess2 介面。</span><span class="sxs-lookup"><span data-stu-id="a3b70-110">This interface logically extends the ICorDebugProcess and ICorDebugProcess2 interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3b70-111">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="a3b70-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3b70-112">需求</span><span class="sxs-lookup"><span data-stu-id="a3b70-112">Requirements</span></span>  
 <span data-ttu-id="a3b70-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a3b70-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3b70-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a3b70-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3b70-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3b70-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3b70-116">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3b70-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3b70-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3b70-117">See also</span></span>

- [<span data-ttu-id="a3b70-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a3b70-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="a3b70-119">偵錯</span><span class="sxs-lookup"><span data-stu-id="a3b70-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
