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
ms.openlocfilehash: c4b4f90f918c872f3227ac22f4cccadcbf3194a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425476"
---
# <a name="inotifyconnection2unregisternotifysource-method"></a><span data-ttu-id="6dc20-102">INotifyConnection2::UnregisterNotifySource 方法</span><span class="sxs-lookup"><span data-stu-id="6dc20-102">INotifyConnection2::UnregisterNotifySource Method</span></span>
<span data-ttu-id="6dc20-103">從連接中移除指定的通知來源物件。</span><span class="sxs-lookup"><span data-stu-id="6dc20-103">Removes a specified notification source object from the connection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dc20-104">語法</span><span class="sxs-lookup"><span data-stu-id="6dc20-104">Syntax</span></span>  
  
```  
HRESULT UnregisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6dc20-105">參數</span><span class="sxs-lookup"><span data-stu-id="6dc20-105">Parameters</span></span>  
 `in_pNotifySource`  
 <span data-ttu-id="6dc20-106">[in]要移除註冊的通知物件。</span><span class="sxs-lookup"><span data-stu-id="6dc20-106">[in] Notification object to be unregistered.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6dc20-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="6dc20-107">Return Value</span></span>  
 <span data-ttu-id="6dc20-108">如果此方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="6dc20-108">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dc20-109">需求</span><span class="sxs-lookup"><span data-stu-id="6dc20-109">Requirements</span></span>  
 <span data-ttu-id="6dc20-110">**標頭：** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="6dc20-110">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dc20-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6dc20-111">See Also</span></span>  
 [<span data-ttu-id="6dc20-112">INotifyConnection2 介面</span><span class="sxs-lookup"><span data-stu-id="6dc20-112">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 [<span data-ttu-id="6dc20-113">INotifySource2 介面</span><span class="sxs-lookup"><span data-stu-id="6dc20-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="6dc20-114">INotifySink2 介面</span><span class="sxs-lookup"><span data-stu-id="6dc20-114">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="6dc20-115">RegisterNotifySource 方法</span><span class="sxs-lookup"><span data-stu-id="6dc20-115">RegisterNotifySource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-registernotifysource-method.md)
