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
ms.openlocfilehash: ecd4ad31b8dad55e9538642a4dc652341bc84b97
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784679"
---
# <a name="icordebugassembly-interface"></a><span data-ttu-id="2a585-102">ICorDebugAssembly 介面</span><span class="sxs-lookup"><span data-stu-id="2a585-102">ICorDebugAssembly Interface</span></span>

<span data-ttu-id="2a585-103">表示組件。</span><span class="sxs-lookup"><span data-stu-id="2a585-103">Represents an assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2a585-104">方法</span><span class="sxs-lookup"><span data-stu-id="2a585-104">Methods</span></span>  
  
|<span data-ttu-id="2a585-105">方法</span><span class="sxs-lookup"><span data-stu-id="2a585-105">Method</span></span>|<span data-ttu-id="2a585-106">描述</span><span class="sxs-lookup"><span data-stu-id="2a585-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2a585-107">EnumerateModules 方法</span><span class="sxs-lookup"><span data-stu-id="2a585-107">EnumerateModules Method</span></span>](icordebugassembly-enumeratemodules-method.md)|<span data-ttu-id="2a585-108">取得元件中所含模組的列舉值。</span><span class="sxs-lookup"><span data-stu-id="2a585-108">Gets an enumerator for the modules contained in the assembly.</span></span>|  
|[<span data-ttu-id="2a585-109">GetAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="2a585-109">GetAppDomain Method</span></span>](icordebugassembly-getappdomain-method.md)|<span data-ttu-id="2a585-110">取得包含這個 `ICorDebugAssembly` 實例之應用程式域的介面指標。</span><span class="sxs-lookup"><span data-stu-id="2a585-110">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>|  
|[<span data-ttu-id="2a585-111">GetCodeBase 方法</span><span class="sxs-lookup"><span data-stu-id="2a585-111">GetCodeBase Method</span></span>](icordebugassembly-getcodebase-method.md)|<span data-ttu-id="2a585-112">未在目前的 .NET Framework 版本中執行。</span><span class="sxs-lookup"><span data-stu-id="2a585-112">Not implemented in the current version of the .NET Framework.</span></span>|  
|[<span data-ttu-id="2a585-113">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="2a585-113">GetName Method</span></span>](icordebugassembly-getname-method.md)|<span data-ttu-id="2a585-114">取得組件名稱。</span><span class="sxs-lookup"><span data-stu-id="2a585-114">Gets the name of the assembly.</span></span>|  
|[<span data-ttu-id="2a585-115">GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="2a585-115">GetProcess Method</span></span>](icordebugassembly-getprocess-method.md)|<span data-ttu-id="2a585-116">取得元件正在其中執行的 ICorDebugProcess 實例。</span><span class="sxs-lookup"><span data-stu-id="2a585-116">Gets the ICorDebugProcess instance in which the assembly is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a585-117">備註</span><span class="sxs-lookup"><span data-stu-id="2a585-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2a585-118">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="2a585-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a585-119">需求</span><span class="sxs-lookup"><span data-stu-id="2a585-119">Requirements</span></span>  
 <span data-ttu-id="2a585-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2a585-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a585-121">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2a585-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a585-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a585-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a585-123">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a585-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a585-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="2a585-124">See also</span></span>

- [<span data-ttu-id="2a585-125">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="2a585-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
