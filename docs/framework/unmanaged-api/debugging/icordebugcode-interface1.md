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
ms.openlocfilehash: 03cbc1a598ba6c0166f72ff404c239763956c996
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687602"
---
# <a name="icordebugcode-interface"></a><span data-ttu-id="fc333-102">ICorDebugCode 介面</span><span class="sxs-lookup"><span data-stu-id="fc333-102">ICorDebugCode Interface</span></span>

<span data-ttu-id="fc333-103">表示 Microsoft Intermediate Language (MSIL) 程式碼或機器碼的區段。</span><span class="sxs-lookup"><span data-stu-id="fc333-103">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fc333-104">方法</span><span class="sxs-lookup"><span data-stu-id="fc333-104">Methods</span></span>  
  
|<span data-ttu-id="fc333-105">方法</span><span class="sxs-lookup"><span data-stu-id="fc333-105">Method</span></span>|<span data-ttu-id="fc333-106">描述</span><span class="sxs-lookup"><span data-stu-id="fc333-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fc333-107">CreateBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="fc333-107">CreateBreakpoint Method</span></span>](icordebugcode-createbreakpoint-method.md)|<span data-ttu-id="fc333-108">在指定的位移處建立中斷點。</span><span class="sxs-lookup"><span data-stu-id="fc333-108">Creates a breakpoint at the specified offset.</span></span>|  
|[<span data-ttu-id="fc333-109">GetAddress 方法</span><span class="sxs-lookup"><span data-stu-id="fc333-109">GetAddress Method</span></span>](icordebugcode-getaddress-method.md)|<span data-ttu-id="fc333-110">取得這個所代表之程式碼區段 (RVA) 的相對虛擬位址 `ICorDebugCode` 。</span><span class="sxs-lookup"><span data-stu-id="fc333-110">Gets the relative virtual address (RVA) of the code segment that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="fc333-111">GetCode 方法</span><span class="sxs-lookup"><span data-stu-id="fc333-111">GetCode Method</span></span>](icordebugcode-getcode-method.md)|<span data-ttu-id="fc333-112">取得指定之函式的所有程式碼，並針對反組解碼進行格式化。</span><span class="sxs-lookup"><span data-stu-id="fc333-112">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="fc333-113">這個方法已被取代;請改用 [ICorDebugCode2：： GetCodeChunks](icordebugcode2-getcodechunks-method.md) 。</span><span class="sxs-lookup"><span data-stu-id="fc333-113">This method has been deprecated; use [ICorDebugCode2::GetCodeChunks](icordebugcode2-getcodechunks-method.md) instead.</span></span>|  
|[<span data-ttu-id="fc333-114">GetEnCRemapSequencePoints 方法</span><span class="sxs-lookup"><span data-stu-id="fc333-114">GetEnCRemapSequencePoints Method</span></span>](icordebugcode-getencremapsequencepoints-method.md)|<span data-ttu-id="fc333-115">未實作。</span><span class="sxs-lookup"><span data-stu-id="fc333-115">Not implemented.</span></span>|  
|[<span data-ttu-id="fc333-116">GetFunction 方法</span><span class="sxs-lookup"><span data-stu-id="fc333-116">GetFunction Method</span></span>](icordebugcode-getfunction-method.md)|<span data-ttu-id="fc333-117">取得與此相關聯的 "ICorDebugFunction" `ICorDebugCode` 。</span><span class="sxs-lookup"><span data-stu-id="fc333-117">Gets the "ICorDebugFunction" associated with this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="fc333-118">GetILToNativeMapping 方法</span><span class="sxs-lookup"><span data-stu-id="fc333-118">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)|<span data-ttu-id="fc333-119">取得 "COR_DEBUG_IL_TO_NATIVE_MAP" 實例的陣列，這些實例表示從 MSIL 位移到原生位移的對應。</span><span class="sxs-lookup"><span data-stu-id="fc333-119">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from MSIL offsets to native offsets.</span></span>|  
|[<span data-ttu-id="fc333-120">GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="fc333-120">GetSize Method</span></span>](icordebugcode-getsize-method.md)|<span data-ttu-id="fc333-121">取得這個所表示之二進位程式碼的大小（以位元組為單位） `ICorDebugCode` 。</span><span class="sxs-lookup"><span data-stu-id="fc333-121">Gets the size, in bytes, of the binary code represented by this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="fc333-122">GetVersionNumber 方法</span><span class="sxs-lookup"><span data-stu-id="fc333-122">GetVersionNumber Method</span></span>](icordebugcode-getversionnumber-method.md)|<span data-ttu-id="fc333-123">取得以一為基礎的數位，識別此所代表的程式碼版本 `ICorDebugCode` 。</span><span class="sxs-lookup"><span data-stu-id="fc333-123">Gets the one-based number that identifies the version of the code that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="fc333-124">IsIL 方法</span><span class="sxs-lookup"><span data-stu-id="fc333-124">IsIL Method</span></span>](icordebugcode-isil-method.md)|<span data-ttu-id="fc333-125">取得值，這個值會指出這個是否 `ICorDebugCode` 會在 MSIL 中進行編譯。</span><span class="sxs-lookup"><span data-stu-id="fc333-125">Gets a value that indicates whether this `ICorDebugCode` is compiled in MSIL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc333-126">備註</span><span class="sxs-lookup"><span data-stu-id="fc333-126">Remarks</span></span>  

 <span data-ttu-id="fc333-127">`ICorDebugCode` 可以代表 MSIL 或機器碼。</span><span class="sxs-lookup"><span data-stu-id="fc333-127">`ICorDebugCode` can represent either MSIL or native code.</span></span> <span data-ttu-id="fc333-128">代表 MSIL 程式碼的 "ICorDebugFunction" 物件可以有零個或一個 `ICorDebugCode` 與其相關聯的物件。</span><span class="sxs-lookup"><span data-stu-id="fc333-128">An "ICorDebugFunction" object that represents MSIL code can have either zero or one `ICorDebugCode` objects associated with it.</span></span> <span data-ttu-id="fc333-129">代表原生程式碼的 "ICorDebugFunction" 物件可以有任意數目的 `ICorDebugCode` 物件與其相關聯。</span><span class="sxs-lookup"><span data-stu-id="fc333-129">An "ICorDebugFunction" object that represents native code can have any number of `ICorDebugCode` objects associated with it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fc333-130">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="fc333-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc333-131">需求</span><span class="sxs-lookup"><span data-stu-id="fc333-131">Requirements</span></span>  

 <span data-ttu-id="fc333-132">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fc333-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc333-133">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc333-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc333-134">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc333-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc333-135">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc333-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc333-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc333-136">See also</span></span>

- [<span data-ttu-id="fc333-137">ICorDebugCode3 介面</span><span class="sxs-lookup"><span data-stu-id="fc333-137">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="fc333-138">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="fc333-138">Debugging Interfaces</span></span>](debugging-interfaces.md)
