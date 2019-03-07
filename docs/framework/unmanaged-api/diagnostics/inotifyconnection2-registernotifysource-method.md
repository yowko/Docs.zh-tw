---
title: INotifyConnection2::RegisterNotifySource 方法
ms.date: 03/30/2017
api_name:
- INotifyConnection2.RegisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::RegisterNotifySource
helpviewer_keywords:
- INotifyConnection2::RegisterNotifySource method [.NET Framework debugging]
- RegisterNotifySource method [.NET Framework debugging]
ms.assetid: 2632da80-6e4b-4429-8dee-b382745a5f81
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0c08cac6fd6b467fe365989cb4d6780325bdaa90
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501613"
---
# <a name="inotifyconnection2registernotifysource-method"></a><span data-ttu-id="47125-102">INotifyConnection2::RegisterNotifySource 方法</span><span class="sxs-lookup"><span data-stu-id="47125-102">INotifyConnection2::RegisterNotifySource Method</span></span>
<span data-ttu-id="47125-103">安裝指定的通知來源。</span><span class="sxs-lookup"><span data-stu-id="47125-103">Installs a specified notification source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47125-104">語法</span><span class="sxs-lookup"><span data-stu-id="47125-104">Syntax</span></span>  
  
```  
HRESULT RegisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource,  
    [out] INotifySink2**   out_ppNotifySink  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47125-105">參數</span><span class="sxs-lookup"><span data-stu-id="47125-105">Parameters</span></span>  
 `in_pNotifySource`  
 <span data-ttu-id="47125-106">[in]指定要做為通知來源物件。</span><span class="sxs-lookup"><span data-stu-id="47125-106">[in] Specifies the object to be used as the notification source.</span></span>  
  
 `out_ppNotifySink`  
 <span data-ttu-id="47125-107">[out]接收要用作通知接收的物件。</span><span class="sxs-lookup"><span data-stu-id="47125-107">[out] Receives the object to be used as the notification sink.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47125-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="47125-108">Return Value</span></span>  
 <span data-ttu-id="47125-109">如果方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="47125-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47125-110">需求</span><span class="sxs-lookup"><span data-stu-id="47125-110">Requirements</span></span>  
 <span data-ttu-id="47125-111">**標頭：** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="47125-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47125-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47125-112">See also</span></span>
- [<span data-ttu-id="47125-113">INotifyConnection2 介面</span><span class="sxs-lookup"><span data-stu-id="47125-113">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [<span data-ttu-id="47125-114">INotifySource2 介面</span><span class="sxs-lookup"><span data-stu-id="47125-114">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="47125-115">INotifySink2 介面</span><span class="sxs-lookup"><span data-stu-id="47125-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="47125-116">UnregisterNotifySource 方法</span><span class="sxs-lookup"><span data-stu-id="47125-116">UnregisterNotifySource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-unregisternotifysource-method.md)
