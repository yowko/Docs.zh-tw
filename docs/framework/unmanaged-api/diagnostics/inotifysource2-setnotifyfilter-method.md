---
title: INotifySource2::SetNotifyFilter 方法
ms.date: 03/30/2017
api_name:
- INotifySource2.SetNotifyFilter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySource2::SetNotifyFilter
helpviewer_keywords:
- INotifySource2::SetNotifyFilter method [.NET Framework debugging]
- SetNotifyFilter method [.NET Framework debugging]
ms.assetid: 6351fc92-b126-4af6-9bf3-0a8ce92845fc
topic_type:
- apiref
ms.openlocfilehash: 99bce831405d722f1f1ca0ae56e60f95f2d905e8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719927"
---
# <a name="inotifysource2setnotifyfilter-method"></a><span data-ttu-id="e8746-102">INotifySource2::SetNotifyFilter 方法</span><span class="sxs-lookup"><span data-stu-id="e8746-102">INotifySource2::SetNotifyFilter Method</span></span>

<span data-ttu-id="e8746-103">指派要用於此來源的通知篩選。</span><span class="sxs-lookup"><span data-stu-id="e8746-103">Assigns a notification filter for use with this source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8746-104">語法</span><span class="sxs-lookup"><span data-stu-id="e8746-104">Syntax</span></span>  
  
```cpp  
HRESULT SetNotifyFilter  
(  
    [in]  NOTIFY_FILTER   in_NotifyFilter,  
    [in]  USER_THREAD*    in_pUserThreadFilter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8746-105">參數</span><span class="sxs-lookup"><span data-stu-id="e8746-105">Parameters</span></span>  

 `in_NotifyFilter`  
 <span data-ttu-id="e8746-106">在 [NOTIFY_FILTER](notify-filter-enumeration.md) 列舉值的位元組合，這些值會識別偵錯工具 API 的回呼。</span><span class="sxs-lookup"><span data-stu-id="e8746-106">[in] A bitwise combination of the [NOTIFY_FILTER](notify-filter-enumeration.md) enumeration values that identify callbacks for the debugger API.</span></span>  
  
 `in_pUserThreadFilter`  
 <span data-ttu-id="e8746-107">在 [USER_THREAD](user-thread-structure.md) 結構的指標，此結構會識別偵錯工具 API 的執行緒。</span><span class="sxs-lookup"><span data-stu-id="e8746-107">[in] A pointer to a [USER_THREAD](user-thread-structure.md) structure that identifies threads for the debugger API.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8746-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="e8746-108">Return Value</span></span>  

 <span data-ttu-id="e8746-109">如果方法成功，則為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="e8746-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8746-110">需求</span><span class="sxs-lookup"><span data-stu-id="e8746-110">Requirements</span></span>  

 <span data-ttu-id="e8746-111">**標頭：** ProtocolNotify2 .idl</span><span class="sxs-lookup"><span data-stu-id="e8746-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8746-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8746-112">See also</span></span>

- [<span data-ttu-id="e8746-113">INotifySource2 介面</span><span class="sxs-lookup"><span data-stu-id="e8746-113">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="e8746-114">INotifyConnection2 介面</span><span class="sxs-lookup"><span data-stu-id="e8746-114">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
- [<span data-ttu-id="e8746-115">INotifySink2 介面</span><span class="sxs-lookup"><span data-stu-id="e8746-115">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
