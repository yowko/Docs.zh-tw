---
title: "ICorDebugLoadedModule 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5cdc89ec81d76a3ce7d39a53e097745d6c9822f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="9faef-102">ICorDebugLoadedModule 介面</span><span class="sxs-lookup"><span data-stu-id="9faef-102">ICorDebugLoadedModule Interface</span></span>
<span data-ttu-id="9faef-103">提供載入模組的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9faef-103">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9faef-104">方法</span><span class="sxs-lookup"><span data-stu-id="9faef-104">Methods</span></span>  
  
|<span data-ttu-id="9faef-105">方法</span><span class="sxs-lookup"><span data-stu-id="9faef-105">Method</span></span>|<span data-ttu-id="9faef-106">說明</span><span class="sxs-lookup"><span data-stu-id="9faef-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9faef-107">GetBaseAddress 方法</span><span class="sxs-lookup"><span data-stu-id="9faef-107">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="9faef-108">取得載入模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="9faef-108">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="9faef-109">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="9faef-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getname-method.md)|<span data-ttu-id="9faef-110">取得載入模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="9faef-110">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="9faef-111">GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="9faef-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="9faef-112">取得載入模組的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="9faef-112">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9faef-113">備註</span><span class="sxs-lookup"><span data-stu-id="9faef-113">Remarks</span></span>  
 <span data-ttu-id="9faef-114">`ICorDebugLoadedModule` 介面是由偵錯工具實作，並由 CLR 偵錯介面用以從偵錯工具取得載入模組的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9faef-114">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9faef-115">這個介面僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="9faef-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="9faef-116">如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。</span><span class="sxs-lookup"><span data-stu-id="9faef-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9faef-117">需求</span><span class="sxs-lookup"><span data-stu-id="9faef-117">Requirements</span></span>  
 <span data-ttu-id="9faef-118">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9faef-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9faef-119">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9faef-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9faef-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9faef-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9faef-121">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9faef-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9faef-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9faef-122">See Also</span></span>  
 [<span data-ttu-id="9faef-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="9faef-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="9faef-124">偵錯</span><span class="sxs-lookup"><span data-stu-id="9faef-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
