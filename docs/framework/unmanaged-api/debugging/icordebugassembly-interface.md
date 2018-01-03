---
title: ICorDebugAssembly Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAssembly
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAssembly
helpviewer_keywords: ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 9d657a28-6984-4c5e-8a54-89d20080baff
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6331c00c2be0805afb56028e9e1a13cd11168cf1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassembly-interface1"></a><span data-ttu-id="5a9e7-102">ICorDebugAssembly Interface1</span><span class="sxs-lookup"><span data-stu-id="5a9e7-102">ICorDebugAssembly Interface1</span></span>
<span data-ttu-id="5a9e7-103">表示組件。</span><span class="sxs-lookup"><span data-stu-id="5a9e7-103">Represents an assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5a9e7-104">方法</span><span class="sxs-lookup"><span data-stu-id="5a9e7-104">Methods</span></span>  
  
|<span data-ttu-id="5a9e7-105">方法</span><span class="sxs-lookup"><span data-stu-id="5a9e7-105">Method</span></span>|<span data-ttu-id="5a9e7-106">描述</span><span class="sxs-lookup"><span data-stu-id="5a9e7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5a9e7-107">EnumerateModules 方法</span><span class="sxs-lookup"><span data-stu-id="5a9e7-107">EnumerateModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)|<span data-ttu-id="5a9e7-108">取得組件中所包含之模組的列舉值。</span><span class="sxs-lookup"><span data-stu-id="5a9e7-108">Gets an enumerator for the modules contained in the assembly.</span></span>|  
|[<span data-ttu-id="5a9e7-109">GetAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="5a9e7-109">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getappdomain-method.md)|<span data-ttu-id="5a9e7-110">取得包含這個應用程式定義域的介面指標`ICorDebugAssembly`執行個體。</span><span class="sxs-lookup"><span data-stu-id="5a9e7-110">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>|  
|[<span data-ttu-id="5a9e7-111">GetCodeBase 方法</span><span class="sxs-lookup"><span data-stu-id="5a9e7-111">GetCodeBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getcodebase-method.md)|<span data-ttu-id="5a9e7-112">不在目前版本的.NET framework 中實作。</span><span class="sxs-lookup"><span data-stu-id="5a9e7-112">Not implemented in the current version of the .NET Framework.</span></span>|  
|[<span data-ttu-id="5a9e7-113">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="5a9e7-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getname-method.md)|<span data-ttu-id="5a9e7-114">取得組件名稱。</span><span class="sxs-lookup"><span data-stu-id="5a9e7-114">Gets the name of the assembly.</span></span>|  
|[<span data-ttu-id="5a9e7-115">GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="5a9e7-115">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getprocess-method.md)|<span data-ttu-id="5a9e7-116">取得該組件正在執行的 ICorDebugProcess 執行個體。</span><span class="sxs-lookup"><span data-stu-id="5a9e7-116">Gets the ICorDebugProcess instance in which the assembly is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a9e7-117">備註</span><span class="sxs-lookup"><span data-stu-id="5a9e7-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a9e7-118">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="5a9e7-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a9e7-119">需求</span><span class="sxs-lookup"><span data-stu-id="5a9e7-119">Requirements</span></span>  
 <span data-ttu-id="5a9e7-120">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5a9e7-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a9e7-121">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a9e7-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a9e7-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a9e7-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a9e7-123">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a9e7-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a9e7-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="5a9e7-124">See Also</span></span>  
 [<span data-ttu-id="5a9e7-125">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="5a9e7-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
