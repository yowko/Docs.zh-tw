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
ms.openlocfilehash: 7d3c0d833208c91c548ea993bb6aa32e36e1f358
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776645"
---
# <a name="inotifyconnection2registernotifysource-method"></a><span data-ttu-id="2dce9-102">INotifyConnection2::RegisterNotifySource 方法</span><span class="sxs-lookup"><span data-stu-id="2dce9-102">INotifyConnection2::RegisterNotifySource Method</span></span>
<span data-ttu-id="2dce9-103">安裝指定的通知來源。</span><span class="sxs-lookup"><span data-stu-id="2dce9-103">Installs a specified notification source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dce9-104">語法</span><span class="sxs-lookup"><span data-stu-id="2dce9-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource,  
    [out] INotifySink2**   out_ppNotifySink  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2dce9-105">參數</span><span class="sxs-lookup"><span data-stu-id="2dce9-105">Parameters</span></span>  
 `in_pNotifySource`  
 <span data-ttu-id="2dce9-106">[in]指定要做為通知來源物件。</span><span class="sxs-lookup"><span data-stu-id="2dce9-106">[in] Specifies the object to be used as the notification source.</span></span>  
  
 `out_ppNotifySink`  
 <span data-ttu-id="2dce9-107">[out]接收要用作通知接收的物件。</span><span class="sxs-lookup"><span data-stu-id="2dce9-107">[out] Receives the object to be used as the notification sink.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2dce9-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="2dce9-108">Return Value</span></span>  
 <span data-ttu-id="2dce9-109">如果方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="2dce9-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2dce9-110">需求</span><span class="sxs-lookup"><span data-stu-id="2dce9-110">Requirements</span></span>  
 <span data-ttu-id="2dce9-111">**標頭：** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="2dce9-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dce9-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2dce9-112">See also</span></span>

- [<span data-ttu-id="2dce9-113">INotifyConnection2 介面</span><span class="sxs-lookup"><span data-stu-id="2dce9-113">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [<span data-ttu-id="2dce9-114">INotifySource2 介面</span><span class="sxs-lookup"><span data-stu-id="2dce9-114">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="2dce9-115">INotifySink2 介面</span><span class="sxs-lookup"><span data-stu-id="2dce9-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="2dce9-116">UnregisterNotifySource 方法</span><span class="sxs-lookup"><span data-stu-id="2dce9-116">UnregisterNotifySource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-unregisternotifysource-method.md)
