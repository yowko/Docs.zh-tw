---
title: ICorDebugCode Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode
helpviewer_keywords:
- ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7bd14fb6-8b54-4484-a891-e3c21859c019
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 86659b624ef01922b6c5d1db9b3ae3697d0128b3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcode-interface1"></a><span data-ttu-id="95dde-102">ICorDebugCode Interface1</span><span class="sxs-lookup"><span data-stu-id="95dde-102">ICorDebugCode Interface1</span></span>
<span data-ttu-id="95dde-103">表示 Microsoft Intermediate Language (MSIL) 程式碼或機器碼的區段。</span><span class="sxs-lookup"><span data-stu-id="95dde-103">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="95dde-104">方法</span><span class="sxs-lookup"><span data-stu-id="95dde-104">Methods</span></span>  
  
|<span data-ttu-id="95dde-105">方法</span><span class="sxs-lookup"><span data-stu-id="95dde-105">Method</span></span>|<span data-ttu-id="95dde-106">描述</span><span class="sxs-lookup"><span data-stu-id="95dde-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="95dde-107">CreateBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="95dde-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-createbreakpoint-method.md)|<span data-ttu-id="95dde-108">建立指定之位移的中斷點。</span><span class="sxs-lookup"><span data-stu-id="95dde-108">Creates a breakpoint at the specified offset.</span></span>|  
|[<span data-ttu-id="95dde-109">GetAddress 方法</span><span class="sxs-lookup"><span data-stu-id="95dde-109">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getaddress-method.md)|<span data-ttu-id="95dde-110">取得程式碼片段的相對虛擬位址 (RVA)，這`ICorDebugCode`代表。</span><span class="sxs-lookup"><span data-stu-id="95dde-110">Gets the relative virtual address (RVA) of the code segment that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="95dde-111">GetCode 方法</span><span class="sxs-lookup"><span data-stu-id="95dde-111">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)|<span data-ttu-id="95dde-112">取得指定的函式，格式為反組譯碼的所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="95dde-112">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="95dde-113">這個方法已被取代。使用[icordebugcode2:: Getcodechunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)改為。</span><span class="sxs-lookup"><span data-stu-id="95dde-113">This method has been deprecated; use [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) instead.</span></span>|  
|[<span data-ttu-id="95dde-114">GetEnCRemapSequencePoints 方法</span><span class="sxs-lookup"><span data-stu-id="95dde-114">GetEnCRemapSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getencremapsequencepoints-method.md)|<span data-ttu-id="95dde-115">未實作。</span><span class="sxs-lookup"><span data-stu-id="95dde-115">Not implemented.</span></span>|  
|[<span data-ttu-id="95dde-116">GetFunction 方法</span><span class="sxs-lookup"><span data-stu-id="95dde-116">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getfunction-method.md)|<span data-ttu-id="95dde-117">取得與此相關聯 「 ICorDebugFunction" `ICorDebugCode`。</span><span class="sxs-lookup"><span data-stu-id="95dde-117">Gets the "ICorDebugFunction" associated with this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="95dde-118">GetILToNativeMapping 方法</span><span class="sxs-lookup"><span data-stu-id="95dde-118">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)|<span data-ttu-id="95dde-119">取得"COR_DEBUG_IL_TO_NATIVE_MAP 」 執行個體，以表示的 MSIL 位移的對應到原生位移的陣列。</span><span class="sxs-lookup"><span data-stu-id="95dde-119">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from MSIL offsets to native offsets.</span></span>|  
|[<span data-ttu-id="95dde-120">GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="95dde-120">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getsize-method.md)|<span data-ttu-id="95dde-121">取得以位元組為單位的二進位的程式碼所代表的大小， `ICorDebugCode`。</span><span class="sxs-lookup"><span data-stu-id="95dde-121">Gets the size, in bytes, of the binary code represented by this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="95dde-122">GetVersionNumber 方法</span><span class="sxs-lookup"><span data-stu-id="95dde-122">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)|<span data-ttu-id="95dde-123">取得識別的程式碼版本 1 為基底數字這個`ICorDebugCode`代表。</span><span class="sxs-lookup"><span data-stu-id="95dde-123">Gets the one-based number that identifies the version of the code that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="95dde-124">IsIL 方法</span><span class="sxs-lookup"><span data-stu-id="95dde-124">IsIL Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-isil-method.md)|<span data-ttu-id="95dde-125">取得值，指出是否此`ICorDebugCode`在 MSIL 中編譯。</span><span class="sxs-lookup"><span data-stu-id="95dde-125">Gets a value that indicates whether this `ICorDebugCode` is compiled in MSIL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95dde-126">備註</span><span class="sxs-lookup"><span data-stu-id="95dde-126">Remarks</span></span>  
 <span data-ttu-id="95dde-127">`ICorDebugCode`可以表示 MSIL 或原生程式碼。</span><span class="sxs-lookup"><span data-stu-id="95dde-127">`ICorDebugCode` can represent either MSIL or native code.</span></span> <span data-ttu-id="95dde-128">表示 MSIL 程式碼的 「 ICorDebugFunction"物件可以有零個或一個`ICorDebugCode`與其相關聯的物件。</span><span class="sxs-lookup"><span data-stu-id="95dde-128">An "ICorDebugFunction" object that represents MSIL code can have either zero or one `ICorDebugCode` objects associated with it.</span></span> <span data-ttu-id="95dde-129">「 ICorDebugFunction 」 物件，表示原生程式碼可以有任意數目的`ICorDebugCode`與其相關聯的物件。</span><span class="sxs-lookup"><span data-stu-id="95dde-129">An "ICorDebugFunction" object that represents native code can have any number of `ICorDebugCode` objects associated with it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="95dde-130">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="95dde-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95dde-131">需求</span><span class="sxs-lookup"><span data-stu-id="95dde-131">Requirements</span></span>  
 <span data-ttu-id="95dde-132">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="95dde-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95dde-133">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="95dde-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95dde-134">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95dde-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95dde-135">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95dde-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95dde-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="95dde-136">See Also</span></span>  
    
 [<span data-ttu-id="95dde-137">ICorDebugCode3 介面</span><span class="sxs-lookup"><span data-stu-id="95dde-137">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 [<span data-ttu-id="95dde-138">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="95dde-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
