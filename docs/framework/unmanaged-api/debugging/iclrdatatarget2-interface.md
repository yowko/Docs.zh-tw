---
title: ICLRDataTarget2 介面
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2
helpviewer_keywords:
- ICLRDataTarget2 interface [.NET Framework debugging]
ms.assetid: 94249397-861b-4294-a538-cf01466a66d3
topic_type:
- apiref
ms.openlocfilehash: dee5108439610b67c3397cebcd8ee5f84d4eacea
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723632"
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="59dd4-102">ICLRDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="59dd4-102">ICLRDataTarget2 Interface</span></span>

<span data-ttu-id="59dd4-103">[ICLRDataTarget](iclrdatatarget-interface.md)的子類別，可供資料存取服務層用來操作目標進程中的虛擬記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="59dd4-103">A subclass of [ICLRDataTarget](iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="59dd4-104">方法</span><span class="sxs-lookup"><span data-stu-id="59dd4-104">Methods</span></span>  
  
|<span data-ttu-id="59dd4-105">方法</span><span class="sxs-lookup"><span data-stu-id="59dd4-105">Method</span></span>|<span data-ttu-id="59dd4-106">描述</span><span class="sxs-lookup"><span data-stu-id="59dd4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="59dd4-107">AllocVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="59dd4-107">AllocVirtual Method</span></span>](iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="59dd4-108">在目標進程的位址空間中配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="59dd4-108">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="59dd4-109">FreeVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="59dd4-109">FreeVirtual Method</span></span>](iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="59dd4-110">釋出先前在目標進程的位址空間中配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="59dd4-110">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59dd4-111">備註</span><span class="sxs-lookup"><span data-stu-id="59dd4-111">Remarks</span></span>  

 <span data-ttu-id="59dd4-112">API 用戶端 (也就是偵錯工具) 必須針對適合的特定目標處理序實作這個介面。</span><span class="sxs-lookup"><span data-stu-id="59dd4-112">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="59dd4-113">例如，即時處理序的實作與記憶體傾印的實作不同。</span><span class="sxs-lookup"><span data-stu-id="59dd4-113">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="59dd4-114">目標可能不支援修改其記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="59dd4-114">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59dd4-115">需求</span><span class="sxs-lookup"><span data-stu-id="59dd4-115">Requirements</span></span>  

 <span data-ttu-id="59dd4-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="59dd4-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59dd4-117">**標頭：** ClrData .idl、ClrData。h</span><span class="sxs-lookup"><span data-stu-id="59dd4-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="59dd4-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59dd4-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59dd4-119">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59dd4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59dd4-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59dd4-120">See also</span></span>

- [<span data-ttu-id="59dd4-121">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="59dd4-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
- [<span data-ttu-id="59dd4-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="59dd4-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
