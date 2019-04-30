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
ms.openlocfilehash: 2f16b4628215bee2410708edeb337b41fbdc0311
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946363"
---
# <a name="icordebuginternalframe-interface"></a><span data-ttu-id="a6690-102">ICorDebugInternalFrame 介面</span><span class="sxs-lookup"><span data-stu-id="a6690-102">ICorDebugInternalFrame Interface</span></span>

<span data-ttu-id="a6690-103">表示執行階段內部的框架在堆疊上。</span><span class="sxs-lookup"><span data-stu-id="a6690-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="a6690-104">這個介面是 ICorDebugFrame 介面的子類別。</span><span class="sxs-lookup"><span data-stu-id="a6690-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a6690-105">方法</span><span class="sxs-lookup"><span data-stu-id="a6690-105">Methods</span></span>  
  
|<span data-ttu-id="a6690-106">方法</span><span class="sxs-lookup"><span data-stu-id="a6690-106">Method</span></span>|<span data-ttu-id="a6690-107">描述</span><span class="sxs-lookup"><span data-stu-id="a6690-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a6690-108">GetFrameType 方法</span><span class="sxs-lookup"><span data-stu-id="a6690-108">GetFrameType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="a6690-109">取得這個內部框架的類型。</span><span class="sxs-lookup"><span data-stu-id="a6690-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6690-110">備註</span><span class="sxs-lookup"><span data-stu-id="a6690-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6690-111">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="a6690-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6690-112">需求</span><span class="sxs-lookup"><span data-stu-id="a6690-112">Requirements</span></span>  
 <span data-ttu-id="a6690-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a6690-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6690-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a6690-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a6690-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6690-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6690-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6690-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6690-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6690-117">See also</span></span>

- [<span data-ttu-id="a6690-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a6690-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
