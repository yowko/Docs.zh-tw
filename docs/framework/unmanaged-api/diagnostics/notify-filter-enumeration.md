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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 63c3ecd0ae0d9e1df62d73eb05b759093583f652
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61915313"
---
# <a name="notifyfilter-enumeration"></a><span data-ttu-id="5d3d1-102">NOTIFY_FILTER 列舉</span><span class="sxs-lookup"><span data-stu-id="5d3d1-102">NOTIFY_FILTER Enumeration</span></span>
<span data-ttu-id="5d3d1-103">識別偵錯工具的函式的回呼。</span><span class="sxs-lookup"><span data-stu-id="5d3d1-103">Identifies callbacks for debugger functions.</span></span> <span data-ttu-id="5d3d1-104">如需詳細資訊，請參閱 < [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="5d3d1-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d3d1-105">語法</span><span class="sxs-lookup"><span data-stu-id="5d3d1-105">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="5d3d1-106">成員</span><span class="sxs-lookup"><span data-stu-id="5d3d1-106">Members</span></span>  
  
|<span data-ttu-id="5d3d1-107">成員</span><span class="sxs-lookup"><span data-stu-id="5d3d1-107">Member</span></span>|<span data-ttu-id="5d3d1-108">描述</span><span class="sxs-lookup"><span data-stu-id="5d3d1-108">Description</span></span>|  
|------------|-----------------|  
|`NOTIFY_FILTER_ONSYNCCALLOUT`|<span data-ttu-id="5d3d1-109">指出[INotifySink2::OnSyncCallOut](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md)應該叫用方法。</span><span class="sxs-lookup"><span data-stu-id="5d3d1-109">Indicates that the [INotifySink2::OnSyncCallOut](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLENTER`|<span data-ttu-id="5d3d1-110">指出[INotifySink2::OnSyncCallEnter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md)應該叫用方法。</span><span class="sxs-lookup"><span data-stu-id="5d3d1-110">Indicates that the [INotifySink2::OnSyncCallEnter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLEXIT`|<span data-ttu-id="5d3d1-111">指出[INotifySink2::OnSyncCallExit](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md)應該叫用方法。</span><span class="sxs-lookup"><span data-stu-id="5d3d1-111">Indicates that the [INotifySink2::OnSyncCallExit](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLRETURN`|<span data-ttu-id="5d3d1-112">指出[INotifySink2::OnSyncCallReturn](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md)應該叫用方法。</span><span class="sxs-lookup"><span data-stu-id="5d3d1-112">Indicates that the [INotifySink2::OnSyncCallReturn](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALLSYNC`|<span data-ttu-id="5d3d1-113">表示所有[INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)應該叫用方法。</span><span class="sxs-lookup"><span data-stu-id="5d3d1-113">Indicates that all of the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) methods should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALL`|<span data-ttu-id="5d3d1-114">啟動所有現有和未來的通知。</span><span class="sxs-lookup"><span data-stu-id="5d3d1-114">Activates all existing and future notifications.</span></span>|  
|`NOTIFY_FILTER_NONE`|<span data-ttu-id="5d3d1-115">表示不應該叫用沒有通知方法。</span><span class="sxs-lookup"><span data-stu-id="5d3d1-115">Indicates that no notification methods should be invoked.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5d3d1-116">需求</span><span class="sxs-lookup"><span data-stu-id="5d3d1-116">Requirements</span></span>  
 <span data-ttu-id="5d3d1-117">**標頭：** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="5d3d1-117">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d3d1-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d3d1-118">See also</span></span>

- [<span data-ttu-id="5d3d1-119">診斷符號存放區列舉</span><span class="sxs-lookup"><span data-stu-id="5d3d1-119">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
