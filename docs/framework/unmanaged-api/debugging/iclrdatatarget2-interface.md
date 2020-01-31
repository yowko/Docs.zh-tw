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
ms.openlocfilehash: bdc8378a129dd5bb1d9fdcb080c7b5cd53d34091
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789067"
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="ce703-102">ICLRDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="ce703-102">ICLRDataTarget2 Interface</span></span>
<span data-ttu-id="ce703-103">資料存取服務層用來操作目標進程中虛擬記憶體區域的[ICLRDataTarget](iclrdatatarget-interface.md)子類別。</span><span class="sxs-lookup"><span data-stu-id="ce703-103">A subclass of [ICLRDataTarget](iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ce703-104">方法</span><span class="sxs-lookup"><span data-stu-id="ce703-104">Methods</span></span>  
  
|<span data-ttu-id="ce703-105">方法</span><span class="sxs-lookup"><span data-stu-id="ce703-105">Method</span></span>|<span data-ttu-id="ce703-106">描述</span><span class="sxs-lookup"><span data-stu-id="ce703-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ce703-107">AllocVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="ce703-107">AllocVirtual Method</span></span>](iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="ce703-108">在目標進程的位址空間中配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="ce703-108">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="ce703-109">FreeVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="ce703-109">FreeVirtual Method</span></span>](iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="ce703-110">釋放先前在目標進程的位址空間中配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="ce703-110">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce703-111">備註</span><span class="sxs-lookup"><span data-stu-id="ce703-111">Remarks</span></span>  
 <span data-ttu-id="ce703-112">API 用戶端 (也就是偵錯工具) 必須針對適合的特定目標處理序實作這個介面。</span><span class="sxs-lookup"><span data-stu-id="ce703-112">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="ce703-113">例如，即時處理序的實作與記憶體傾印的實作不同。</span><span class="sxs-lookup"><span data-stu-id="ce703-113">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="ce703-114">目標可能不支援修改其記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="ce703-114">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce703-115">需求</span><span class="sxs-lookup"><span data-stu-id="ce703-115">Requirements</span></span>  
 <span data-ttu-id="ce703-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ce703-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce703-117">**標頭：** ClrData .idl，ClrData。h</span><span class="sxs-lookup"><span data-stu-id="ce703-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="ce703-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce703-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce703-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce703-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce703-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="ce703-120">See also</span></span>

- [<span data-ttu-id="ce703-121">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="ce703-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
- [<span data-ttu-id="ce703-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="ce703-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
