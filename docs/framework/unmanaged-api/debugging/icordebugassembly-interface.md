---
title: ICorDebugAssembly 介面
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly
helpviewer_keywords:
- ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 9d657a28-6984-4c5e-8a54-89d20080baff
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 426269d14992ae0f1f8c02619b259cfdd4bcbf8f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959445"
---
# <a name="icordebugassembly-interface"></a><span data-ttu-id="eb45a-102">ICorDebugAssembly 介面</span><span class="sxs-lookup"><span data-stu-id="eb45a-102">ICorDebugAssembly Interface</span></span>

<span data-ttu-id="eb45a-103">表示組件。</span><span class="sxs-lookup"><span data-stu-id="eb45a-103">Represents an assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eb45a-104">方法</span><span class="sxs-lookup"><span data-stu-id="eb45a-104">Methods</span></span>  
  
|<span data-ttu-id="eb45a-105">方法</span><span class="sxs-lookup"><span data-stu-id="eb45a-105">Method</span></span>|<span data-ttu-id="eb45a-106">說明</span><span class="sxs-lookup"><span data-stu-id="eb45a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eb45a-107">EnumerateModules 方法</span><span class="sxs-lookup"><span data-stu-id="eb45a-107">EnumerateModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)|<span data-ttu-id="eb45a-108">取得元件中所含模組的列舉值。</span><span class="sxs-lookup"><span data-stu-id="eb45a-108">Gets an enumerator for the modules contained in the assembly.</span></span>|  
|[<span data-ttu-id="eb45a-109">GetAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="eb45a-109">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getappdomain-method.md)|<span data-ttu-id="eb45a-110">取得包含這個`ICorDebugAssembly`實例之應用程式域的介面指標。</span><span class="sxs-lookup"><span data-stu-id="eb45a-110">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>|  
|[<span data-ttu-id="eb45a-111">GetCodeBase 方法</span><span class="sxs-lookup"><span data-stu-id="eb45a-111">GetCodeBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getcodebase-method.md)|<span data-ttu-id="eb45a-112">未在目前的 .NET Framework 版本中執行。</span><span class="sxs-lookup"><span data-stu-id="eb45a-112">Not implemented in the current version of the .NET Framework.</span></span>|  
|[<span data-ttu-id="eb45a-113">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="eb45a-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getname-method.md)|<span data-ttu-id="eb45a-114">取得組件名稱。</span><span class="sxs-lookup"><span data-stu-id="eb45a-114">Gets the name of the assembly.</span></span>|  
|[<span data-ttu-id="eb45a-115">GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="eb45a-115">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getprocess-method.md)|<span data-ttu-id="eb45a-116">取得元件正在其中執行的 ICorDebugProcess 實例。</span><span class="sxs-lookup"><span data-stu-id="eb45a-116">Gets the ICorDebugProcess instance in which the assembly is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb45a-117">備註</span><span class="sxs-lookup"><span data-stu-id="eb45a-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eb45a-118">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="eb45a-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb45a-119">需求</span><span class="sxs-lookup"><span data-stu-id="eb45a-119">Requirements</span></span>  
 <span data-ttu-id="eb45a-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eb45a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb45a-121">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eb45a-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eb45a-122">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb45a-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb45a-123">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb45a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb45a-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb45a-124">See also</span></span>

- [<span data-ttu-id="eb45a-125">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="eb45a-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
