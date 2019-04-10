---
title: INotifyConnection2::UnregisterNotifySource 方法
ms.date: 03/30/2017
api_name:
- INotifyConnection2.UnregisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::UnregisterNotifySource
helpviewer_keywords:
- INotifyConnection2::UnregisterNotifySource method [.NET Framework debugging]
- UnregisterNotifySource method [.NET Framework debugging]
ms.assetid: 2fc6c715-646f-41fd-9c12-c59b40575269
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 742be1467d2f1e6eb7d8567ddf85f8e65ea4b8d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229455"
---
# <a name="inotifyconnection2unregisternotifysource-method"></a><span data-ttu-id="91d93-102">INotifyConnection2::UnregisterNotifySource 方法</span><span class="sxs-lookup"><span data-stu-id="91d93-102">INotifyConnection2::UnregisterNotifySource Method</span></span>
<span data-ttu-id="91d93-103">從連接中移除指定的通知來源物件。</span><span class="sxs-lookup"><span data-stu-id="91d93-103">Removes a specified notification source object from the connection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91d93-104">語法</span><span class="sxs-lookup"><span data-stu-id="91d93-104">Syntax</span></span>  
  
```  
HRESULT UnregisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91d93-105">參數</span><span class="sxs-lookup"><span data-stu-id="91d93-105">Parameters</span></span>  
 `in_pNotifySource`  
 <span data-ttu-id="91d93-106">[in]要取消註冊的通知物件。</span><span class="sxs-lookup"><span data-stu-id="91d93-106">[in] Notification object to be unregistered.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91d93-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="91d93-107">Return Value</span></span>  
 <span data-ttu-id="91d93-108">如果方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="91d93-108">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91d93-109">需求</span><span class="sxs-lookup"><span data-stu-id="91d93-109">Requirements</span></span>  
 <span data-ttu-id="91d93-110">**標頭：** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="91d93-110">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91d93-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91d93-111">See also</span></span>

- [<span data-ttu-id="91d93-112">INotifyConnection2 介面</span><span class="sxs-lookup"><span data-stu-id="91d93-112">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [<span data-ttu-id="91d93-113">INotifySource2 介面</span><span class="sxs-lookup"><span data-stu-id="91d93-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="91d93-114">INotifySink2 介面</span><span class="sxs-lookup"><span data-stu-id="91d93-114">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="91d93-115">RegisterNotifySource 方法</span><span class="sxs-lookup"><span data-stu-id="91d93-115">RegisterNotifySource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-registernotifysource-method.md)
