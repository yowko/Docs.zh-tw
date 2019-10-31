---
title: ICLRDataTarget 介面
ms.date: 03/30/2017
api_name:
- ICLRDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget
helpviewer_keywords:
- ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: e2f05155-9bef-4e11-b703-7f05890665ca
topic_type:
- apiref
ms.openlocfilehash: 51b246e45b8bbdf809f5e90ac2bc29ca724751fc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73113496"
---
# <a name="iclrdatatarget-interface"></a><span data-ttu-id="23381-102">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="23381-102">ICLRDataTarget Interface</span></span>
<span data-ttu-id="23381-103">提供與 common language runtime （CLR）的目標專案互動的方法。</span><span class="sxs-lookup"><span data-stu-id="23381-103">Provides methods for interaction with a target item of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="23381-104">方法</span><span class="sxs-lookup"><span data-stu-id="23381-104">Methods</span></span>  
  
|<span data-ttu-id="23381-105">方法</span><span class="sxs-lookup"><span data-stu-id="23381-105">Method</span></span>|<span data-ttu-id="23381-106">描述</span><span class="sxs-lookup"><span data-stu-id="23381-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="23381-107">GetCurrentThreadID 方法</span><span class="sxs-lookup"><span data-stu-id="23381-107">GetCurrentThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getcurrentthreadid-method.md)|<span data-ttu-id="23381-108">取得目前線程的作業系統識別碼。</span><span class="sxs-lookup"><span data-stu-id="23381-108">Gets the operating system identifier for the current thread.</span></span>|  
|[<span data-ttu-id="23381-109">GetImageBase 方法</span><span class="sxs-lookup"><span data-stu-id="23381-109">GetImageBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getimagebase-method.md)|<span data-ttu-id="23381-110">取得指定之映射的基底記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="23381-110">Gets the base memory address for the specified image.</span></span>|  
|[<span data-ttu-id="23381-111">GetMachineType 方法</span><span class="sxs-lookup"><span data-stu-id="23381-111">GetMachineType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getmachinetype-method.md)|<span data-ttu-id="23381-112">取得目標進程所使用之指令集種類的識別碼。</span><span class="sxs-lookup"><span data-stu-id="23381-112">Gets an identifier for the kind of instruction set that the target process is using.</span></span>|  
|[<span data-ttu-id="23381-113">GetPointerSize 方法</span><span class="sxs-lookup"><span data-stu-id="23381-113">GetPointerSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getpointersize-method.md)|<span data-ttu-id="23381-114">取得目前目標的指標大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="23381-114">Gets the size, in bytes, of a pointer to the current target.</span></span>|  
|[<span data-ttu-id="23381-115">GetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="23381-115">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getthreadcontext-method.md)|<span data-ttu-id="23381-116">取得具有指定識別碼之執行緒內容的指標。</span><span class="sxs-lookup"><span data-stu-id="23381-116">Gets a pointer to the context of the thread with the specified identifier.</span></span>|  
|[<span data-ttu-id="23381-117">GetTLSValue 方法</span><span class="sxs-lookup"><span data-stu-id="23381-117">GetTLSValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-gettlsvalue-method.md)|<span data-ttu-id="23381-118">取得指定執行緒之指定索引處的執行緒區域儲存區（TLS）中的值。</span><span class="sxs-lookup"><span data-stu-id="23381-118">Gets a value in thread local storage (TLS) at the specified index for the specified thread.</span></span>|  
|[<span data-ttu-id="23381-119">ReadVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="23381-119">ReadVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-readvirtual-method.md)|<span data-ttu-id="23381-120">將資料從指定的虛擬記憶體位址讀入指定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="23381-120">Reads data from the specified virtual memory address into the specified buffer.</span></span>|  
|[<span data-ttu-id="23381-121">Request 方法</span><span class="sxs-lookup"><span data-stu-id="23381-121">Request Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-request-method.md)|<span data-ttu-id="23381-122">由 common language runtime （CLR）資料存取服務呼叫，以要求作業，如實作為所定義。</span><span class="sxs-lookup"><span data-stu-id="23381-122">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>|  
|[<span data-ttu-id="23381-123">SetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="23381-123">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-setthreadcontext-method.md)|<span data-ttu-id="23381-124">設定目標進程中指定之執行緒的目前內容。</span><span class="sxs-lookup"><span data-stu-id="23381-124">Sets the current context of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="23381-125">SetTLSValue 方法</span><span class="sxs-lookup"><span data-stu-id="23381-125">SetTLSValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-settlsvalue-method.md)|<span data-ttu-id="23381-126">設定目標進程中指定執行緒的執行緒區域儲存區（TLS）中的值。</span><span class="sxs-lookup"><span data-stu-id="23381-126">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="23381-127">WriteVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="23381-127">WriteVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-writevirtual-method.md)|<span data-ttu-id="23381-128">將資料從指定的緩衝區寫入指定的虛擬記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="23381-128">Writes data from the specified buffer to the specified virtual memory address.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23381-129">備註</span><span class="sxs-lookup"><span data-stu-id="23381-129">Remarks</span></span>  
 <span data-ttu-id="23381-130">API 用戶端（也就是偵錯工具）必須針對特定目標專案，實作為適當的介面。</span><span class="sxs-lookup"><span data-stu-id="23381-130">The API client (that is, the debugger) must implement this interface as appropriate for the particular target item.</span></span> <span data-ttu-id="23381-131">例如，即時處理序的實作與記憶體傾印的實作不同。</span><span class="sxs-lookup"><span data-stu-id="23381-131">For example, a live process would have an implementation different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23381-132">需求</span><span class="sxs-lookup"><span data-stu-id="23381-132">Requirements</span></span>  
 <span data-ttu-id="23381-133">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="23381-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23381-134">**標頭：** ClrData .idl，ClrData。h</span><span class="sxs-lookup"><span data-stu-id="23381-134">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="23381-135">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23381-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23381-136">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23381-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23381-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="23381-137">See also</span></span>

- [<span data-ttu-id="23381-138">ICLRDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="23381-138">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [<span data-ttu-id="23381-139">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="23381-139">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
