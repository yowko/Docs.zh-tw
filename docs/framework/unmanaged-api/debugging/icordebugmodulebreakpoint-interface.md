---
title: ICorDebugModuleBreakpoint Interface
ms.date: 03/30/2017
api_name:
- ICorDebugModuleBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleBreakpoint
helpviewer_keywords:
- ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: 34667162-f314-475f-ae1b-ce9cb0fcbb83
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6a43a264fcaa94ce4e629d8db504e9d416f6b89
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179708"
---
# <a name="icordebugmodulebreakpoint-interface"></a><span data-ttu-id="d0401-102">ICorDebugModuleBreakpoint Interface</span><span class="sxs-lookup"><span data-stu-id="d0401-102">ICorDebugModuleBreakpoint Interface</span></span>

<span data-ttu-id="d0401-103">提供特定模組的存取。</span><span class="sxs-lookup"><span data-stu-id="d0401-103">Provides access to specific modules.</span></span> <span data-ttu-id="d0401-104">這個介面是 ICorDebugBreakpoint 介面的子類別。</span><span class="sxs-lookup"><span data-stu-id="d0401-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d0401-105">方法</span><span class="sxs-lookup"><span data-stu-id="d0401-105">Methods</span></span>  
  
|<span data-ttu-id="d0401-106">方法</span><span class="sxs-lookup"><span data-stu-id="d0401-106">Method</span></span>|<span data-ttu-id="d0401-107">描述</span><span class="sxs-lookup"><span data-stu-id="d0401-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d0401-108">GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="d0401-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="d0401-109">取得參考的模組設定此中斷點的位置 ICorDebugModule 介面指標。</span><span class="sxs-lookup"><span data-stu-id="d0401-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0401-110">備註</span><span class="sxs-lookup"><span data-stu-id="d0401-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0401-111">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="d0401-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0401-112">需求</span><span class="sxs-lookup"><span data-stu-id="d0401-112">Requirements</span></span>  
 <span data-ttu-id="d0401-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d0401-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0401-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d0401-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0401-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0401-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d0401-116">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="d0401-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d0401-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0401-117">See also</span></span>

- [<span data-ttu-id="d0401-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d0401-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
