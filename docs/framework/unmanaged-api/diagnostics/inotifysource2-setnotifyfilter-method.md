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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: abe1c8881330ebba5f7b68452cf3db0666ac20c3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736240"
---
# <a name="inotifysource2setnotifyfilter-method"></a><span data-ttu-id="bddfa-102">INotifySource2::SetNotifyFilter 方法</span><span class="sxs-lookup"><span data-stu-id="bddfa-102">INotifySource2::SetNotifyFilter Method</span></span>
<span data-ttu-id="bddfa-103">會指定與此來源使用的通知篩選器。</span><span class="sxs-lookup"><span data-stu-id="bddfa-103">Assigns a notification filter for use with this source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bddfa-104">語法</span><span class="sxs-lookup"><span data-stu-id="bddfa-104">Syntax</span></span>  
  
```cpp  
HRESULT SetNotifyFilter  
(  
    [in]  NOTIFY_FILTER   in_NotifyFilter,  
    [in]  USER_THREAD*    in_pUserThreadFilter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bddfa-105">參數</span><span class="sxs-lookup"><span data-stu-id="bddfa-105">Parameters</span></span>  
 `in_NotifyFilter`  
 <span data-ttu-id="bddfa-106">[in]位元組合[NOTIFY_FILTER](../../../../docs/framework/unmanaged-api/diagnostics/notify-filter-enumeration.md)識別回呼偵錯工具 API 的列舉值。</span><span class="sxs-lookup"><span data-stu-id="bddfa-106">[in] A bitwise combination of the [NOTIFY_FILTER](../../../../docs/framework/unmanaged-api/diagnostics/notify-filter-enumeration.md) enumeration values that identify callbacks for the debugger API.</span></span>  
  
 `in_pUserThreadFilter`  
 <span data-ttu-id="bddfa-107">[in]指標[USER_THREAD](../../../../docs/framework/unmanaged-api/diagnostics/user-thread-structure.md)識別執行緒偵錯工具 API 的結構。</span><span class="sxs-lookup"><span data-stu-id="bddfa-107">[in] A pointer to a [USER_THREAD](../../../../docs/framework/unmanaged-api/diagnostics/user-thread-structure.md) structure that identifies threads for the debugger API.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bddfa-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="bddfa-108">Return Value</span></span>  
 <span data-ttu-id="bddfa-109">如果方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="bddfa-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bddfa-110">需求</span><span class="sxs-lookup"><span data-stu-id="bddfa-110">Requirements</span></span>  
 <span data-ttu-id="bddfa-111">**標頭：** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="bddfa-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bddfa-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bddfa-112">See also</span></span>

- [<span data-ttu-id="bddfa-113">INotifySource2 介面</span><span class="sxs-lookup"><span data-stu-id="bddfa-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="bddfa-114">INotifyConnection2 介面</span><span class="sxs-lookup"><span data-stu-id="bddfa-114">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [<span data-ttu-id="bddfa-115">INotifySink2 介面</span><span class="sxs-lookup"><span data-stu-id="bddfa-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
