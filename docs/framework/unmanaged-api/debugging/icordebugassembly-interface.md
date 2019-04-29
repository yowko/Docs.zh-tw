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
ms.openlocfilehash: 3dd60defc1c003fa4b235ddcb0a78b9a819b1b0c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645523"
---
# <a name="icordebugassembly-interface"></a><span data-ttu-id="5157b-102">ICorDebugAssembly 介面</span><span class="sxs-lookup"><span data-stu-id="5157b-102">ICorDebugAssembly Interface</span></span>

<span data-ttu-id="5157b-103">表示組件。</span><span class="sxs-lookup"><span data-stu-id="5157b-103">Represents an assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5157b-104">方法</span><span class="sxs-lookup"><span data-stu-id="5157b-104">Methods</span></span>  
  
|<span data-ttu-id="5157b-105">方法</span><span class="sxs-lookup"><span data-stu-id="5157b-105">Method</span></span>|<span data-ttu-id="5157b-106">描述</span><span class="sxs-lookup"><span data-stu-id="5157b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5157b-107">EnumerateModules 方法</span><span class="sxs-lookup"><span data-stu-id="5157b-107">EnumerateModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)|<span data-ttu-id="5157b-108">取得組件中所包含之模組的列舉值。</span><span class="sxs-lookup"><span data-stu-id="5157b-108">Gets an enumerator for the modules contained in the assembly.</span></span>|  
|[<span data-ttu-id="5157b-109">GetAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="5157b-109">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getappdomain-method.md)|<span data-ttu-id="5157b-110">取得包含這個應用程式定義域的介面指標`ICorDebugAssembly`執行個體。</span><span class="sxs-lookup"><span data-stu-id="5157b-110">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>|  
|[<span data-ttu-id="5157b-111">GetCodeBase 方法</span><span class="sxs-lookup"><span data-stu-id="5157b-111">GetCodeBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getcodebase-method.md)|<span data-ttu-id="5157b-112">不在目前版本的.NET framework 中實作。</span><span class="sxs-lookup"><span data-stu-id="5157b-112">Not implemented in the current version of the .NET Framework.</span></span>|  
|[<span data-ttu-id="5157b-113">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="5157b-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getname-method.md)|<span data-ttu-id="5157b-114">取得組件名稱。</span><span class="sxs-lookup"><span data-stu-id="5157b-114">Gets the name of the assembly.</span></span>|  
|[<span data-ttu-id="5157b-115">GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="5157b-115">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getprocess-method.md)|<span data-ttu-id="5157b-116">取得 ICorDebugProcess 執行個體執行所在的組件。</span><span class="sxs-lookup"><span data-stu-id="5157b-116">Gets the ICorDebugProcess instance in which the assembly is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5157b-117">備註</span><span class="sxs-lookup"><span data-stu-id="5157b-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5157b-118">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="5157b-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5157b-119">需求</span><span class="sxs-lookup"><span data-stu-id="5157b-119">Requirements</span></span>  
 <span data-ttu-id="5157b-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5157b-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5157b-121">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5157b-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5157b-122">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5157b-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5157b-123">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5157b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5157b-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5157b-124">See also</span></span>

- [<span data-ttu-id="5157b-125">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="5157b-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
