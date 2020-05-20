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
ms.openlocfilehash: 7ba9f68e102696da107b5cb782c76cb55ed95ee6
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441964"
---
# <a name="inotifysource2setnotifyfilter-method"></a><span data-ttu-id="30ee3-102">INotifySource2::SetNotifyFilter 方法</span><span class="sxs-lookup"><span data-stu-id="30ee3-102">INotifySource2::SetNotifyFilter Method</span></span>
<span data-ttu-id="30ee3-103">指派要與此來源搭配使用的通知篩選準則。</span><span class="sxs-lookup"><span data-stu-id="30ee3-103">Assigns a notification filter for use with this source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30ee3-104">語法</span><span class="sxs-lookup"><span data-stu-id="30ee3-104">Syntax</span></span>  
  
```cpp  
HRESULT SetNotifyFilter  
(  
    [in]  NOTIFY_FILTER   in_NotifyFilter,  
    [in]  USER_THREAD*    in_pUserThreadFilter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30ee3-105">參數</span><span class="sxs-lookup"><span data-stu-id="30ee3-105">Parameters</span></span>  
 `in_NotifyFilter`  
 <span data-ttu-id="30ee3-106">在[NOTIFY_FILTER](notify-filter-enumeration.md)列舉值的位元組合，識別偵錯工具 API 的回呼。</span><span class="sxs-lookup"><span data-stu-id="30ee3-106">[in] A bitwise combination of the [NOTIFY_FILTER](notify-filter-enumeration.md) enumeration values that identify callbacks for the debugger API.</span></span>  
  
 `in_pUserThreadFilter`  
 <span data-ttu-id="30ee3-107">在識別偵錯工具 API 執行緒之[USER_THREAD](user-thread-structure.md)結構的指標。</span><span class="sxs-lookup"><span data-stu-id="30ee3-107">[in] A pointer to a [USER_THREAD](user-thread-structure.md) structure that identifies threads for the debugger API.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30ee3-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="30ee3-108">Return Value</span></span>  
 <span data-ttu-id="30ee3-109">如果方法成功，則 S_OK。</span><span class="sxs-lookup"><span data-stu-id="30ee3-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30ee3-110">需求</span><span class="sxs-lookup"><span data-stu-id="30ee3-110">Requirements</span></span>  
 <span data-ttu-id="30ee3-111">**標頭：** ProtocolNotify2 .idl</span><span class="sxs-lookup"><span data-stu-id="30ee3-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30ee3-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30ee3-112">See also</span></span>

- [<span data-ttu-id="30ee3-113">INotifySource2 介面</span><span class="sxs-lookup"><span data-stu-id="30ee3-113">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="30ee3-114">INotifyConnection2 介面</span><span class="sxs-lookup"><span data-stu-id="30ee3-114">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
- [<span data-ttu-id="30ee3-115">INotifySink2 介面</span><span class="sxs-lookup"><span data-stu-id="30ee3-115">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
