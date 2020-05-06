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
ms.openlocfilehash: af944a9c2bb04f37b06f27cfbe38e23c9613d768
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860410"
---
# <a name="iclrdatatarget3-interface"></a><span data-ttu-id="0d9e8-102">ICLRDataTarget3 介面</span><span class="sxs-lookup"><span data-stu-id="0d9e8-102">ICLRDataTarget3 Interface</span></span>
<span data-ttu-id="0d9e8-103">[ICLRDataTarget2](iclrdatatarget2-interface.md)的子類別，可提供例外狀況資訊的存取權。</span><span class="sxs-lookup"><span data-stu-id="0d9e8-103">A subclass of [ICLRDataTarget2](iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0d9e8-104">方法</span><span class="sxs-lookup"><span data-stu-id="0d9e8-104">Methods</span></span>  
  
|<span data-ttu-id="0d9e8-105">方法</span><span class="sxs-lookup"><span data-stu-id="0d9e8-105">Method</span></span>|<span data-ttu-id="0d9e8-106">描述</span><span class="sxs-lookup"><span data-stu-id="0d9e8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0d9e8-107">GetExceptionRecord 方法</span><span class="sxs-lookup"><span data-stu-id="0d9e8-107">GetExceptionRecord Method</span></span>](iclrdatatarget3-getexceptionrecord-method.md)|<span data-ttu-id="0d9e8-108">由通用語言執行平台 (CLR) 資料存取服務呼叫，用於擷取與目標處理序相關聯的例外狀況記錄。</span><span class="sxs-lookup"><span data-stu-id="0d9e8-108">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span>|  
|[<span data-ttu-id="0d9e8-109">GetExceptionContextRecord 方法</span><span class="sxs-lookup"><span data-stu-id="0d9e8-109">GetExceptionContextRecord Method</span></span>](iclrdatatarget3-getexceptioncontextrecord-method.md)|<span data-ttu-id="0d9e8-110">由 CLR 資料存取服務呼叫，用於擷取與目標處理序相關聯的內容記錄。</span><span class="sxs-lookup"><span data-stu-id="0d9e8-110">Called by the CLR data access services to retrieve the context record associated with the target process.</span></span>|  
|[<span data-ttu-id="0d9e8-111">GetExceptionThreadID 方法</span><span class="sxs-lookup"><span data-stu-id="0d9e8-111">GetExceptionThreadID Method</span></span>](iclrdatatarget3-getexceptionthreadid-method.md)|<span data-ttu-id="0d9e8-112">由 CLR 資料存取服務呼叫以取得擲出例外狀況的執行緒 ID。</span><span class="sxs-lookup"><span data-stu-id="0d9e8-112">Called by the CLR data access services to get the ID of the thread that threw the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d9e8-113">備註</span><span class="sxs-lookup"><span data-stu-id="0d9e8-113">Remarks</span></span>  
 <span data-ttu-id="0d9e8-114">API 用戶端 (也就是偵錯工具) 必須針對適合的特定目標處理序實作這個介面。</span><span class="sxs-lookup"><span data-stu-id="0d9e8-114">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="0d9e8-115">例如，即時處理序的實作與記憶體傾印的實作不同。</span><span class="sxs-lookup"><span data-stu-id="0d9e8-115">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="0d9e8-116">目標可能不支援修改其記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="0d9e8-116">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d9e8-117">需求</span><span class="sxs-lookup"><span data-stu-id="0d9e8-117">Requirements</span></span>  
 <span data-ttu-id="0d9e8-118">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0d9e8-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d9e8-119">**標頭：** ClrData .idl，ClrData。h</span><span class="sxs-lookup"><span data-stu-id="0d9e8-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="0d9e8-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d9e8-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d9e8-121">**.NET Framework 版本：**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0d9e8-121">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d9e8-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="0d9e8-122">See also</span></span>

- [<span data-ttu-id="0d9e8-123">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="0d9e8-123">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
- [<span data-ttu-id="0d9e8-124">ICLRDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="0d9e8-124">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="0d9e8-125">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="0d9e8-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
