---
title: ICorDebugAssembly2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly2
helpviewer_keywords:
- ICorDebugAssembly2 interface [.NET Framework debugging]
ms.assetid: c0766e29-e573-4f9a-a928-167d1de5aa7e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b42cb2bff677963c44bfc04f8bdd6c60497e4731
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909892"
---
# <a name="icordebugassembly2-interface"></a><span data-ttu-id="da4a2-102">ICorDebugAssembly2 介面</span><span class="sxs-lookup"><span data-stu-id="da4a2-102">ICorDebugAssembly2 Interface</span></span>

<span data-ttu-id="da4a2-103">表示組件。</span><span class="sxs-lookup"><span data-stu-id="da4a2-103">Represents an assembly.</span></span> <span data-ttu-id="da4a2-104">這個介面是 ICorDebugAssembly 介面的延伸。</span><span class="sxs-lookup"><span data-stu-id="da4a2-104">This interface is an extension of the ICorDebugAssembly interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="da4a2-105">方法</span><span class="sxs-lookup"><span data-stu-id="da4a2-105">Methods</span></span>  
  
|<span data-ttu-id="da4a2-106">方法</span><span class="sxs-lookup"><span data-stu-id="da4a2-106">Method</span></span>|<span data-ttu-id="da4a2-107">描述</span><span class="sxs-lookup"><span data-stu-id="da4a2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="da4a2-108">IsFullyTrusted 方法</span><span class="sxs-lookup"><span data-stu-id="da4a2-108">IsFullyTrusted Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly2-isfullytrusted-method.md)|<span data-ttu-id="da4a2-109">取得值, 指出執行時間安全性系統是否已授與元件完全信任。</span><span class="sxs-lookup"><span data-stu-id="da4a2-109">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da4a2-110">備註</span><span class="sxs-lookup"><span data-stu-id="da4a2-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="da4a2-111">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="da4a2-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da4a2-112">需求</span><span class="sxs-lookup"><span data-stu-id="da4a2-112">Requirements</span></span>  
 <span data-ttu-id="da4a2-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="da4a2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da4a2-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="da4a2-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da4a2-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da4a2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da4a2-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da4a2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da4a2-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da4a2-117">See also</span></span>

- [<span data-ttu-id="da4a2-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="da4a2-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
