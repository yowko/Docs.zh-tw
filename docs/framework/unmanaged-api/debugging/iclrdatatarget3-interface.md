---
title: ICLRDataTarget3 介面
ms.date: 03/30/2017
api_name:
- ICLRDataTarget3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: d2711bdf-64b3-404c-a0c3-01ba4907f703
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 974abb123c4c11f6bb512431cea5cc6460a5c55a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654735"
---
# <a name="iclrdatatarget3-interface"></a><span data-ttu-id="e7f0a-102">ICLRDataTarget3 介面</span><span class="sxs-lookup"><span data-stu-id="e7f0a-102">ICLRDataTarget3 Interface</span></span>
<span data-ttu-id="e7f0a-103">子類別[ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)提供例外狀況資訊的存取權。</span><span class="sxs-lookup"><span data-stu-id="e7f0a-103">A subclass of [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e7f0a-104">方法</span><span class="sxs-lookup"><span data-stu-id="e7f0a-104">Methods</span></span>  
  
|<span data-ttu-id="e7f0a-105">方法</span><span class="sxs-lookup"><span data-stu-id="e7f0a-105">Method</span></span>|<span data-ttu-id="e7f0a-106">描述</span><span class="sxs-lookup"><span data-stu-id="e7f0a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e7f0a-107">GetExceptionRecord 方法</span><span class="sxs-lookup"><span data-stu-id="e7f0a-107">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)|<span data-ttu-id="e7f0a-108">由通用語言執行平台 (CLR) 資料存取服務呼叫，用於擷取與目標處理序相關聯的例外狀況記錄。</span><span class="sxs-lookup"><span data-stu-id="e7f0a-108">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span>|  
|[<span data-ttu-id="e7f0a-109">GetExceptionContextRecord 方法</span><span class="sxs-lookup"><span data-stu-id="e7f0a-109">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)|<span data-ttu-id="e7f0a-110">由 CLR 資料存取服務呼叫，用於擷取與目標處理序相關聯的內容記錄。</span><span class="sxs-lookup"><span data-stu-id="e7f0a-110">Called by the CLR data access services to retrieve the context record associated with the target process.</span></span>|  
|[<span data-ttu-id="e7f0a-111">GetExceptionThreadID 方法</span><span class="sxs-lookup"><span data-stu-id="e7f0a-111">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)|<span data-ttu-id="e7f0a-112">由 CLR 資料存取服務呼叫以取得擲出例外狀況的執行緒 ID。</span><span class="sxs-lookup"><span data-stu-id="e7f0a-112">Called by the CLR data access services to get the ID of the thread that threw the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7f0a-113">備註</span><span class="sxs-lookup"><span data-stu-id="e7f0a-113">Remarks</span></span>  
 <span data-ttu-id="e7f0a-114">API 用戶端 (也就是偵錯工具) 必須針對適合的特定目標處理序實作這個介面。</span><span class="sxs-lookup"><span data-stu-id="e7f0a-114">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="e7f0a-115">例如，即時處理序的實作與記憶體傾印的實作不同。</span><span class="sxs-lookup"><span data-stu-id="e7f0a-115">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="e7f0a-116">目標可能不支援修改其記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="e7f0a-116">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7f0a-117">需求</span><span class="sxs-lookup"><span data-stu-id="e7f0a-117">Requirements</span></span>  
 <span data-ttu-id="e7f0a-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e7f0a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7f0a-119">**標頭：** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="e7f0a-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="e7f0a-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7f0a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7f0a-121">**.NET framework 版本：**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7f0a-121">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7f0a-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7f0a-122">See also</span></span>
- [<span data-ttu-id="e7f0a-123">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="e7f0a-123">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
- [<span data-ttu-id="e7f0a-124">ICLRDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="e7f0a-124">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [<span data-ttu-id="e7f0a-125">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e7f0a-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
