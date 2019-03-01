---
title: ICorDebugCode 介面
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ca47eb5508907297a78dba1ab2b0a6d2b8ece0d
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976924"
---
# <a name="icordebugcode-interface"></a><span data-ttu-id="ce980-102">ICorDebugCode 介面</span><span class="sxs-lookup"><span data-stu-id="ce980-102">ICorDebugCode Interface</span></span>

<span data-ttu-id="ce980-103">表示 Microsoft Intermediate Language (MSIL) 程式碼或機器碼的區段。</span><span class="sxs-lookup"><span data-stu-id="ce980-103">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ce980-104">方法</span><span class="sxs-lookup"><span data-stu-id="ce980-104">Methods</span></span>  
  
|<span data-ttu-id="ce980-105">方法</span><span class="sxs-lookup"><span data-stu-id="ce980-105">Method</span></span>|<span data-ttu-id="ce980-106">描述</span><span class="sxs-lookup"><span data-stu-id="ce980-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ce980-107">CreateBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="ce980-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-createbreakpoint-method.md)|<span data-ttu-id="ce980-108">建立指定之位移的中斷點。</span><span class="sxs-lookup"><span data-stu-id="ce980-108">Creates a breakpoint at the specified offset.</span></span>|  
|[<span data-ttu-id="ce980-109">GetAddress 方法</span><span class="sxs-lookup"><span data-stu-id="ce980-109">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getaddress-method.md)|<span data-ttu-id="ce980-110">取得程式碼片段的相對虛擬位址 (RVA)，這`ICorDebugCode`表示。</span><span class="sxs-lookup"><span data-stu-id="ce980-110">Gets the relative virtual address (RVA) of the code segment that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="ce980-111">GetCode 方法</span><span class="sxs-lookup"><span data-stu-id="ce980-111">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)|<span data-ttu-id="ce980-112">取得指定的函式，針對 反組譯碼格式化的所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="ce980-112">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="ce980-113">此方法已被取代;使用  [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)改。</span><span class="sxs-lookup"><span data-stu-id="ce980-113">This method has been deprecated; use [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) instead.</span></span>|  
|[<span data-ttu-id="ce980-114">GetEnCRemapSequencePoints 方法</span><span class="sxs-lookup"><span data-stu-id="ce980-114">GetEnCRemapSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getencremapsequencepoints-method.md)|<span data-ttu-id="ce980-115">未實作。</span><span class="sxs-lookup"><span data-stu-id="ce980-115">Not implemented.</span></span>|  
|[<span data-ttu-id="ce980-116">GetFunction 方法</span><span class="sxs-lookup"><span data-stu-id="ce980-116">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getfunction-method.md)|<span data-ttu-id="ce980-117">取得與此相關聯 「 ICorDebugFunction" `ICorDebugCode`。</span><span class="sxs-lookup"><span data-stu-id="ce980-117">Gets the "ICorDebugFunction" associated with this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="ce980-118">GetILToNativeMapping 方法</span><span class="sxs-lookup"><span data-stu-id="ce980-118">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)|<span data-ttu-id="ce980-119">取得"COR_DEBUG_IL_TO_NATIVE_MAP 」 執行個體，表示對應的 MSIL 位移到原生位移陣列。</span><span class="sxs-lookup"><span data-stu-id="ce980-119">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from MSIL offsets to native offsets.</span></span>|  
|[<span data-ttu-id="ce980-120">GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="ce980-120">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getsize-method.md)|<span data-ttu-id="ce980-121">取得以位元組為單位所表示的二進位程式碼的大小， `ICorDebugCode`。</span><span class="sxs-lookup"><span data-stu-id="ce980-121">Gets the size, in bytes, of the binary code represented by this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="ce980-122">GetVersionNumber 方法</span><span class="sxs-lookup"><span data-stu-id="ce980-122">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)|<span data-ttu-id="ce980-123">取得以一為基的數字的程式碼版本識別這個`ICorDebugCode`表示。</span><span class="sxs-lookup"><span data-stu-id="ce980-123">Gets the one-based number that identifies the version of the code that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="ce980-124">IsIL 方法</span><span class="sxs-lookup"><span data-stu-id="ce980-124">IsIL Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-isil-method.md)|<span data-ttu-id="ce980-125">取得值，指出是否此`ICorDebugCode`編譯的 MSIL。</span><span class="sxs-lookup"><span data-stu-id="ce980-125">Gets a value that indicates whether this `ICorDebugCode` is compiled in MSIL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce980-126">備註</span><span class="sxs-lookup"><span data-stu-id="ce980-126">Remarks</span></span>  
 <span data-ttu-id="ce980-127">`ICorDebugCode` 可以表示 MSIL 或原生程式碼。</span><span class="sxs-lookup"><span data-stu-id="ce980-127">`ICorDebugCode` can represent either MSIL or native code.</span></span> <span data-ttu-id="ce980-128">表示 MSIL 程式碼的 「 ICorDebugFunction"物件可以有零個或一個`ICorDebugCode`與其相關聯的物件。</span><span class="sxs-lookup"><span data-stu-id="ce980-128">An "ICorDebugFunction" object that represents MSIL code can have either zero or one `ICorDebugCode` objects associated with it.</span></span> <span data-ttu-id="ce980-129">表示原生程式碼的 「 ICorDebugFunction"物件可以有任意數目的`ICorDebugCode`與其相關聯的物件。</span><span class="sxs-lookup"><span data-stu-id="ce980-129">An "ICorDebugFunction" object that represents native code can have any number of `ICorDebugCode` objects associated with it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce980-130">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="ce980-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce980-131">需求</span><span class="sxs-lookup"><span data-stu-id="ce980-131">Requirements</span></span>  
 <span data-ttu-id="ce980-132">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ce980-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce980-133">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ce980-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce980-134">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce980-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce980-135">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce980-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce980-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce980-136">See also</span></span>

- [<span data-ttu-id="ce980-137">ICorDebugCode3 介面</span><span class="sxs-lookup"><span data-stu-id="ce980-137">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="ce980-138">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="ce980-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
