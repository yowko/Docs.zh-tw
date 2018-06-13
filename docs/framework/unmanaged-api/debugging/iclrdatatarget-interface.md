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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0a5abe8877c8414443fadc00e223df240721132
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33410438"
---
# <a name="iclrdatatarget-interface"></a><span data-ttu-id="17a02-102">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="17a02-102">ICLRDataTarget Interface</span></span>
<span data-ttu-id="17a02-103">提供 common language runtime (CLR) 的目標項目互動的方法。</span><span class="sxs-lookup"><span data-stu-id="17a02-103">Provides methods for interaction with a target item of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="17a02-104">方法</span><span class="sxs-lookup"><span data-stu-id="17a02-104">Methods</span></span>  
  
|<span data-ttu-id="17a02-105">方法</span><span class="sxs-lookup"><span data-stu-id="17a02-105">Method</span></span>|<span data-ttu-id="17a02-106">描述</span><span class="sxs-lookup"><span data-stu-id="17a02-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="17a02-107">GetCurrentThreadID 方法</span><span class="sxs-lookup"><span data-stu-id="17a02-107">GetCurrentThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getcurrentthreadid-method.md)|<span data-ttu-id="17a02-108">取得目前執行緒的作業系統識別項。</span><span class="sxs-lookup"><span data-stu-id="17a02-108">Gets the operating system identifier for the current thread.</span></span>|  
|[<span data-ttu-id="17a02-109">GetImageBase 方法</span><span class="sxs-lookup"><span data-stu-id="17a02-109">GetImageBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getimagebase-method.md)|<span data-ttu-id="17a02-110">取得指定的映像的基底的記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="17a02-110">Gets the base memory address for the specified image.</span></span>|  
|[<span data-ttu-id="17a02-111">GetMachineType 方法</span><span class="sxs-lookup"><span data-stu-id="17a02-111">GetMachineType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getmachinetype-method.md)|<span data-ttu-id="17a02-112">取得目標處理序正在使用的指令集類型的識別項。</span><span class="sxs-lookup"><span data-stu-id="17a02-112">Gets an identifier for the kind of instruction set that the target process is using.</span></span>|  
|[<span data-ttu-id="17a02-113">GetPointerSize 方法</span><span class="sxs-lookup"><span data-stu-id="17a02-113">GetPointerSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getpointersize-method.md)|<span data-ttu-id="17a02-114">取得大小，以位元組為單位的目前目標的指標。</span><span class="sxs-lookup"><span data-stu-id="17a02-114">Gets the size, in bytes, of a pointer to the current target.</span></span>|  
|[<span data-ttu-id="17a02-115">GetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="17a02-115">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getthreadcontext-method.md)|<span data-ttu-id="17a02-116">取得具有指定識別碼的執行緒內容的指標。</span><span class="sxs-lookup"><span data-stu-id="17a02-116">Gets a pointer to the context of the thread with the specified identifier.</span></span>|  
|[<span data-ttu-id="17a02-117">GetTLSValue 方法</span><span class="sxs-lookup"><span data-stu-id="17a02-117">GetTLSValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-gettlsvalue-method.md)|<span data-ttu-id="17a02-118">執行緒區域儲存區 (TLS) 中取得值，指定執行緒的指定索引處。</span><span class="sxs-lookup"><span data-stu-id="17a02-118">Gets a value in thread local storage (TLS) at the specified index for the specified thread.</span></span>|  
|[<span data-ttu-id="17a02-119">ReadVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="17a02-119">ReadVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-readvirtual-method.md)|<span data-ttu-id="17a02-120">從指定的虛擬記憶體位址將資料讀入指定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="17a02-120">Reads data from the specified virtual memory address into the specified buffer.</span></span>|  
|[<span data-ttu-id="17a02-121">Request 方法</span><span class="sxs-lookup"><span data-stu-id="17a02-121">Request Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-request-method.md)|<span data-ttu-id="17a02-122">由通用語言執行平台 (CLR) 資料存取服務要求的操作，實作所定義。</span><span class="sxs-lookup"><span data-stu-id="17a02-122">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>|  
|[<span data-ttu-id="17a02-123">SetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="17a02-123">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-setthreadcontext-method.md)|<span data-ttu-id="17a02-124">目標處理序中，設定指定之執行緒的目前內容。</span><span class="sxs-lookup"><span data-stu-id="17a02-124">Sets the current context of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="17a02-125">SetTLSValue 方法</span><span class="sxs-lookup"><span data-stu-id="17a02-125">SetTLSValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-settlsvalue-method.md)|<span data-ttu-id="17a02-126">執行緒區域儲存區 (TLS) 的目標處理序中指定的執行緒中設定的值。</span><span class="sxs-lookup"><span data-stu-id="17a02-126">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="17a02-127">WriteVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="17a02-127">WriteVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-writevirtual-method.md)|<span data-ttu-id="17a02-128">將資料從指定的緩衝區寫入指定的虛擬記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="17a02-128">Writes data from the specified buffer to the specified virtual memory address.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17a02-129">備註</span><span class="sxs-lookup"><span data-stu-id="17a02-129">Remarks</span></span>  
 <span data-ttu-id="17a02-130">API 用戶端 （也就是偵錯工具） 必須實作此介面適用於特定的目標項目。</span><span class="sxs-lookup"><span data-stu-id="17a02-130">The API client (that is, the debugger) must implement this interface as appropriate for the particular target item.</span></span> <span data-ttu-id="17a02-131">例如，即時處理序的實作與記憶體傾印的實作不同。</span><span class="sxs-lookup"><span data-stu-id="17a02-131">For example, a live process would have an implementation different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17a02-132">需求</span><span class="sxs-lookup"><span data-stu-id="17a02-132">Requirements</span></span>  
 <span data-ttu-id="17a02-133">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="17a02-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17a02-134">**標頭：** ClrData.idl、 ClrData.h</span><span class="sxs-lookup"><span data-stu-id="17a02-134">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="17a02-135">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17a02-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17a02-136">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17a02-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17a02-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17a02-137">See Also</span></span>  
 [<span data-ttu-id="17a02-138">ICLRDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="17a02-138">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [<span data-ttu-id="17a02-139">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="17a02-139">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
