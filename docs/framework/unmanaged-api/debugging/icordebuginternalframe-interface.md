---
title: ICorDebugInternalFrame 介面
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame
helpviewer_keywords:
- ICorDebugInternalFrame interface [.NET Framework debugging]
ms.assetid: bb4772ca-0d54-4185-b738-7a6ffe9ea85a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9764cdcd07a09f5192a8f43b9baa5be40305c40b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910161"
---
# <a name="icordebuginternalframe-interface"></a><span data-ttu-id="eaec8-102">ICorDebugInternalFrame 介面</span><span class="sxs-lookup"><span data-stu-id="eaec8-102">ICorDebugInternalFrame Interface</span></span>

<span data-ttu-id="eaec8-103">表示堆疊上的執行時間內部框架。</span><span class="sxs-lookup"><span data-stu-id="eaec8-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="eaec8-104">這個介面是 ICorDebugFrame 介面的子類別。</span><span class="sxs-lookup"><span data-stu-id="eaec8-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eaec8-105">方法</span><span class="sxs-lookup"><span data-stu-id="eaec8-105">Methods</span></span>  
  
|<span data-ttu-id="eaec8-106">方法</span><span class="sxs-lookup"><span data-stu-id="eaec8-106">Method</span></span>|<span data-ttu-id="eaec8-107">描述</span><span class="sxs-lookup"><span data-stu-id="eaec8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eaec8-108">GetFrameType 方法</span><span class="sxs-lookup"><span data-stu-id="eaec8-108">GetFrameType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="eaec8-109">取得此內部框架的類型。</span><span class="sxs-lookup"><span data-stu-id="eaec8-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eaec8-110">備註</span><span class="sxs-lookup"><span data-stu-id="eaec8-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eaec8-111">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="eaec8-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eaec8-112">需求</span><span class="sxs-lookup"><span data-stu-id="eaec8-112">Requirements</span></span>  
 <span data-ttu-id="eaec8-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eaec8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eaec8-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eaec8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eaec8-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eaec8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eaec8-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eaec8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaec8-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eaec8-117">See also</span></span>

- [<span data-ttu-id="eaec8-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="eaec8-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
