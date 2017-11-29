---
title: "NOTIFY_FILTER 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: NOTIFY_FILTER
api_location: diasymreader.dll
api_type: COM
f1_keywords: NOTIFY_FILTER
helpviewer_keywords: NOTIFY_FILTER enumeration [.NET Framework debugging]
ms.assetid: 4789d08f-8683-45d3-ac30-73d48c61e470
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9db03458aab60d28efe52edfd9830da7862fcb8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="notifyfilter-enumeration"></a><span data-ttu-id="e94b7-102">NOTIFY_FILTER 列舉</span><span class="sxs-lookup"><span data-stu-id="e94b7-102">NOTIFY_FILTER Enumeration</span></span>
<span data-ttu-id="e94b7-103">識別偵錯工具功能的回呼。</span><span class="sxs-lookup"><span data-stu-id="e94b7-103">Identifies callbacks for debugger functions.</span></span> <span data-ttu-id="e94b7-104">如需詳細資訊，請參閱[inotifysource2:: Setnotifyfilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="e94b7-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e94b7-105">語法</span><span class="sxs-lookup"><span data-stu-id="e94b7-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="e94b7-106">成員</span><span class="sxs-lookup"><span data-stu-id="e94b7-106">Members</span></span>  
  
|<span data-ttu-id="e94b7-107">成員</span><span class="sxs-lookup"><span data-stu-id="e94b7-107">Member</span></span>|<span data-ttu-id="e94b7-108">說明</span><span class="sxs-lookup"><span data-stu-id="e94b7-108">Description</span></span>|  
|------------|-----------------|  
|`NOTIFY_FILTER_ONSYNCCALLOUT`|<span data-ttu-id="e94b7-109">表示[inotifysink2:: Onsynccallout](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md)叫用方法。</span><span class="sxs-lookup"><span data-stu-id="e94b7-109">Indicates that the [INotifySink2::OnSyncCallOut](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLENTER`|<span data-ttu-id="e94b7-110">表示[inotifysink2:: Onsynccallenter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md)叫用方法。</span><span class="sxs-lookup"><span data-stu-id="e94b7-110">Indicates that the [INotifySink2::OnSyncCallEnter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLEXIT`|<span data-ttu-id="e94b7-111">表示[inotifysink2:: Onsynccallexit](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md)叫用方法。</span><span class="sxs-lookup"><span data-stu-id="e94b7-111">Indicates that the [INotifySink2::OnSyncCallExit](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLRETURN`|<span data-ttu-id="e94b7-112">表示[inotifysink2:: Onsynccallreturn](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md)叫用方法。</span><span class="sxs-lookup"><span data-stu-id="e94b7-112">Indicates that the [INotifySink2::OnSyncCallReturn](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALLSYNC`|<span data-ttu-id="e94b7-113">表示所有[INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)叫用方法。</span><span class="sxs-lookup"><span data-stu-id="e94b7-113">Indicates that all of the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) methods should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALL`|<span data-ttu-id="e94b7-114">啟動所有的現有及未來通知。</span><span class="sxs-lookup"><span data-stu-id="e94b7-114">Activates all existing and future notifications.</span></span>|  
|`NOTIFY_FILTER_NONE`|<span data-ttu-id="e94b7-115">指出應叫用任何通知方法。</span><span class="sxs-lookup"><span data-stu-id="e94b7-115">Indicates that no notification methods should be invoked.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e94b7-116">需求</span><span class="sxs-lookup"><span data-stu-id="e94b7-116">Requirements</span></span>  
 <span data-ttu-id="e94b7-117">**標頭：** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="e94b7-117">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e94b7-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e94b7-118">See Also</span></span>  
 [<span data-ttu-id="e94b7-119">診斷符號存放區列舉型別</span><span class="sxs-lookup"><span data-stu-id="e94b7-119">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
