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
ms.openlocfilehash: 0d3e6a95d8fd71a67b97923dac53c1f615dfe666
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703417"
---
# <a name="iclrdatatarget-interface"></a><span data-ttu-id="e0198-102">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="e0198-102">ICLRDataTarget Interface</span></span>

<span data-ttu-id="e0198-103">提供與 common language runtime (CLR) 的目標專案互動的方法。</span><span class="sxs-lookup"><span data-stu-id="e0198-103">Provides methods for interaction with a target item of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e0198-104">方法</span><span class="sxs-lookup"><span data-stu-id="e0198-104">Methods</span></span>  
  
|<span data-ttu-id="e0198-105">方法</span><span class="sxs-lookup"><span data-stu-id="e0198-105">Method</span></span>|<span data-ttu-id="e0198-106">描述</span><span class="sxs-lookup"><span data-stu-id="e0198-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e0198-107">GetCurrentThreadID 方法</span><span class="sxs-lookup"><span data-stu-id="e0198-107">GetCurrentThreadID Method</span></span>](iclrdatatarget-getcurrentthreadid-method.md)|<span data-ttu-id="e0198-108">取得目前線程的作業系統識別碼。</span><span class="sxs-lookup"><span data-stu-id="e0198-108">Gets the operating system identifier for the current thread.</span></span>|  
|[<span data-ttu-id="e0198-109">GetImageBase 方法</span><span class="sxs-lookup"><span data-stu-id="e0198-109">GetImageBase Method</span></span>](iclrdatatarget-getimagebase-method.md)|<span data-ttu-id="e0198-110">取得指定之影像的基底記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="e0198-110">Gets the base memory address for the specified image.</span></span>|  
|[<span data-ttu-id="e0198-111">GetMachineType 方法</span><span class="sxs-lookup"><span data-stu-id="e0198-111">GetMachineType Method</span></span>](iclrdatatarget-getmachinetype-method.md)|<span data-ttu-id="e0198-112">取得目標進程正在使用之指令集種類的識別碼。</span><span class="sxs-lookup"><span data-stu-id="e0198-112">Gets an identifier for the kind of instruction set that the target process is using.</span></span>|  
|[<span data-ttu-id="e0198-113">GetPointerSize 方法</span><span class="sxs-lookup"><span data-stu-id="e0198-113">GetPointerSize Method</span></span>](iclrdatatarget-getpointersize-method.md)|<span data-ttu-id="e0198-114">取得目前目標指標的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="e0198-114">Gets the size, in bytes, of a pointer to the current target.</span></span>|  
|[<span data-ttu-id="e0198-115">GetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="e0198-115">GetThreadContext Method</span></span>](iclrdatatarget-getthreadcontext-method.md)|<span data-ttu-id="e0198-116">取得具有指定識別碼之執行緒內容的指標。</span><span class="sxs-lookup"><span data-stu-id="e0198-116">Gets a pointer to the context of the thread with the specified identifier.</span></span>|  
|[<span data-ttu-id="e0198-117">GetTLSValue 方法</span><span class="sxs-lookup"><span data-stu-id="e0198-117">GetTLSValue Method</span></span>](iclrdatatarget-gettlsvalue-method.md)|<span data-ttu-id="e0198-118">取得執行緒區域儲存區中的值， (TLS) 位於指定之執行緒的指定索引處。</span><span class="sxs-lookup"><span data-stu-id="e0198-118">Gets a value in thread local storage (TLS) at the specified index for the specified thread.</span></span>|  
|[<span data-ttu-id="e0198-119">ReadVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="e0198-119">ReadVirtual Method</span></span>](iclrdatatarget-readvirtual-method.md)|<span data-ttu-id="e0198-120">將資料從指定的虛擬記憶體位址讀入指定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="e0198-120">Reads data from the specified virtual memory address into the specified buffer.</span></span>|  
|[<span data-ttu-id="e0198-121">Request 方法</span><span class="sxs-lookup"><span data-stu-id="e0198-121">Request Method</span></span>](iclrdatatarget-request-method.md)|<span data-ttu-id="e0198-122">由 common language runtime 呼叫 (CLR) 資料存取服務來要求作業，如實作為所定義。</span><span class="sxs-lookup"><span data-stu-id="e0198-122">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>|  
|[<span data-ttu-id="e0198-123">SetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="e0198-123">SetThreadContext Method</span></span>](iclrdatatarget-setthreadcontext-method.md)|<span data-ttu-id="e0198-124">在目標進程中，設定指定之執行緒的目前內容。</span><span class="sxs-lookup"><span data-stu-id="e0198-124">Sets the current context of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="e0198-125">SetTLSValue 方法</span><span class="sxs-lookup"><span data-stu-id="e0198-125">SetTLSValue Method</span></span>](iclrdatatarget-settlsvalue-method.md)|<span data-ttu-id="e0198-126">設定執行緒區域儲存區中的值， (目標進程中指定之執行緒的 TLS) 。</span><span class="sxs-lookup"><span data-stu-id="e0198-126">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="e0198-127">WriteVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="e0198-127">WriteVirtual Method</span></span>](iclrdatatarget-writevirtual-method.md)|<span data-ttu-id="e0198-128">將資料從指定的緩衝區寫入至指定的虛擬記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="e0198-128">Writes data from the specified buffer to the specified virtual memory address.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0198-129">備註</span><span class="sxs-lookup"><span data-stu-id="e0198-129">Remarks</span></span>  

 <span data-ttu-id="e0198-130">API 用戶端 (也就是偵錯工具) 必須適當地針對特定目標專案執行這個介面。</span><span class="sxs-lookup"><span data-stu-id="e0198-130">The API client (that is, the debugger) must implement this interface as appropriate for the particular target item.</span></span> <span data-ttu-id="e0198-131">例如，即時處理序的實作與記憶體傾印的實作不同。</span><span class="sxs-lookup"><span data-stu-id="e0198-131">For example, a live process would have an implementation different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0198-132">需求</span><span class="sxs-lookup"><span data-stu-id="e0198-132">Requirements</span></span>  

 <span data-ttu-id="e0198-133">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e0198-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0198-134">**標頭：** ClrData .idl、ClrData。h</span><span class="sxs-lookup"><span data-stu-id="e0198-134">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="e0198-135">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0198-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0198-136">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0198-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0198-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0198-137">See also</span></span>

- [<span data-ttu-id="e0198-138">ICLRDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="e0198-138">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="e0198-139">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e0198-139">Debugging Interfaces</span></span>](debugging-interfaces.md)
