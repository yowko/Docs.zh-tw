---
title: NOTIFY_FILTER 列舉
ms.date: 03/30/2017
api_name:
- NOTIFY_FILTER
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- NOTIFY_FILTER
helpviewer_keywords:
- NOTIFY_FILTER enumeration [.NET Framework debugging]
ms.assetid: 4789d08f-8683-45d3-ac30-73d48c61e470
topic_type:
- apiref
ms.openlocfilehash: 365bc0dc73b04d3afd171c40f336432f77552b6d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690950"
---
# <a name="notify_filter-enumeration"></a><span data-ttu-id="6321b-102">NOTIFY_FILTER 列舉</span><span class="sxs-lookup"><span data-stu-id="6321b-102">NOTIFY_FILTER Enumeration</span></span>

<span data-ttu-id="6321b-103">識別偵錯工具函數的回呼。</span><span class="sxs-lookup"><span data-stu-id="6321b-103">Identifies callbacks for debugger functions.</span></span> <span data-ttu-id="6321b-104">如需詳細資訊，請參閱 [INotifySource2：： SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="6321b-104">For more information, see the [INotifySource2::SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6321b-105">語法</span><span class="sxs-lookup"><span data-stu-id="6321b-105">Syntax</span></span>  
  
```cpp  
enum tagNOTIFY_FILTER  
{  
    NOTIFY_FILTER_ONSYNCCALLOUT    = 0x1,  
    NOTIFY_FILTER_ONSYNCCALLENTER  = 0x2,  
    NOTIFY_FILTER_ONSYNCCALLEXIT   = 0x4,  
    NOTIFY_FILTER_ONSYNCCALLRETURN = 0x8,  
    NOTIFY_FILTER_ALLSYNC = NOTIFY_FILTER_ONSYNCCALLOUT | NOTIFY_FILTER_ONSYNCCALLENTER | NOTIFY_FILTER_ONSYNCCALLEXIT | NOTIFY_FILTER_ONSYNCCALLRETURN,  
    NOTIFY_FILTER_ALL              = 0xffffffff,  
    NOTIFY_FILTER_NONE             = 0  
};  
```  
  
## <a name="members"></a><span data-ttu-id="6321b-106">成員</span><span class="sxs-lookup"><span data-stu-id="6321b-106">Members</span></span>  
  
|<span data-ttu-id="6321b-107">member</span><span class="sxs-lookup"><span data-stu-id="6321b-107">Member</span></span>|<span data-ttu-id="6321b-108">描述</span><span class="sxs-lookup"><span data-stu-id="6321b-108">Description</span></span>|  
|------------|-----------------|  
|`NOTIFY_FILTER_ONSYNCCALLOUT`|<span data-ttu-id="6321b-109">表示應該叫用 [INotifySink2：： OnSyncCallOut](inotifysink2-onsynccallout-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="6321b-109">Indicates that the [INotifySink2::OnSyncCallOut](inotifysink2-onsynccallout-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLENTER`|<span data-ttu-id="6321b-110">表示應該叫用 [INotifySink2：： OnSyncCallEnter](inotifysink2-onsynccallenter-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="6321b-110">Indicates that the [INotifySink2::OnSyncCallEnter](inotifysink2-onsynccallenter-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLEXIT`|<span data-ttu-id="6321b-111">表示應該叫用 [INotifySink2：： OnSyncCallExit](inotifysink2-onsynccallexit-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="6321b-111">Indicates that the [INotifySink2::OnSyncCallExit](inotifysink2-onsynccallexit-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLRETURN`|<span data-ttu-id="6321b-112">表示應該叫用 [INotifySink2：： OnSyncCallReturn](inotifysink2-onsynccallreturn-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="6321b-112">Indicates that the [INotifySink2::OnSyncCallReturn](inotifysink2-onsynccallreturn-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALLSYNC`|<span data-ttu-id="6321b-113">表示應該叫用所有的 [INotifySink2](inotifysink2-interface.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="6321b-113">Indicates that all of the [INotifySink2](inotifysink2-interface.md) methods should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALL`|<span data-ttu-id="6321b-114">啟用所有現有和未來的通知。</span><span class="sxs-lookup"><span data-stu-id="6321b-114">Activates all existing and future notifications.</span></span>|  
|`NOTIFY_FILTER_NONE`|<span data-ttu-id="6321b-115">指出不應該叫用任何通知方法。</span><span class="sxs-lookup"><span data-stu-id="6321b-115">Indicates that no notification methods should be invoked.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6321b-116">需求</span><span class="sxs-lookup"><span data-stu-id="6321b-116">Requirements</span></span>  

 <span data-ttu-id="6321b-117">**標頭：** ProtocolNotify2 .idl</span><span class="sxs-lookup"><span data-stu-id="6321b-117">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6321b-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6321b-118">See also</span></span>

- [<span data-ttu-id="6321b-119">診斷符號存放區列舉</span><span class="sxs-lookup"><span data-stu-id="6321b-119">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)
