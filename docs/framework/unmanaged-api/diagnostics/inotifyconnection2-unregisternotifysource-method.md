---
title: "INotifyConnection2::UnregisterNotifySource 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: INotifyConnection2.UnregisterNotifySource
api_location: diasymreader.dll
api_type: COM
f1_keywords: INotifyConnection2::UnregisterNotifySource
helpviewer_keywords:
- INotifyConnection2::UnregisterNotifySource method [.NET Framework debugging]
- UnregisterNotifySource method [.NET Framework debugging]
ms.assetid: 2fc6c715-646f-41fd-9c12-c59b40575269
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 063a146d31031f0cb14e00278819e8cd874f98c4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="inotifyconnection2unregisternotifysource-method"></a><span data-ttu-id="3203a-102">INotifyConnection2::UnregisterNotifySource 方法</span><span class="sxs-lookup"><span data-stu-id="3203a-102">INotifyConnection2::UnregisterNotifySource Method</span></span>
<span data-ttu-id="3203a-103">從連接中移除指定的通知來源物件。</span><span class="sxs-lookup"><span data-stu-id="3203a-103">Removes a specified notification source object from the connection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3203a-104">語法</span><span class="sxs-lookup"><span data-stu-id="3203a-104">Syntax</span></span>  
  
```  
HRESULT UnregisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3203a-105">參數</span><span class="sxs-lookup"><span data-stu-id="3203a-105">Parameters</span></span>  
 `in_pNotifySource`  
 <span data-ttu-id="3203a-106">[in]要移除註冊的通知物件。</span><span class="sxs-lookup"><span data-stu-id="3203a-106">[in] Notification object to be unregistered.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3203a-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="3203a-107">Return Value</span></span>  
 <span data-ttu-id="3203a-108">如果此方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="3203a-108">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3203a-109">需求</span><span class="sxs-lookup"><span data-stu-id="3203a-109">Requirements</span></span>  
 <span data-ttu-id="3203a-110">**標頭：** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="3203a-110">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3203a-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3203a-111">See Also</span></span>  
 [<span data-ttu-id="3203a-112">INotifyConnection2 介面</span><span class="sxs-lookup"><span data-stu-id="3203a-112">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 [<span data-ttu-id="3203a-113">INotifySource2 介面</span><span class="sxs-lookup"><span data-stu-id="3203a-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="3203a-114">INotifySink2 介面</span><span class="sxs-lookup"><span data-stu-id="3203a-114">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="3203a-115">RegisterNotifySource 方法</span><span class="sxs-lookup"><span data-stu-id="3203a-115">RegisterNotifySource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-registernotifysource-method.md)
