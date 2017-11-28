---
title: "INotifySink2::OnSyncCallOut 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: INotifySink2.OnSyncCallOut
api_location: diasymreader.dll
api_type: COM
f1_keywords: INotifySink2::OnSyncCallOut
helpviewer_keywords:
- INotifySink2::OnSyncCallOut method [.NET Framework debugging]
- OnSyncCallOut method [.NET Framework debugging]
ms.assetid: 97f15656-8677-4079-8553-a1d8603355d6
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 427b54a66b92ef23572739d6c9e0dfd5731eb638
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="inotifysink2onsynccallout-method"></a><span data-ttu-id="3eb7a-102">INotifySink2::OnSyncCallOut 方法</span><span class="sxs-lookup"><span data-stu-id="3eb7a-102">INotifySink2::OnSyncCallOut Method</span></span>
<span data-ttu-id="3eb7a-103">取得叫用時呼叫外。</span><span class="sxs-lookup"><span data-stu-id="3eb7a-103">Gets invoked when a call is out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eb7a-104">語法</span><span class="sxs-lookup"><span data-stu-id="3eb7a-104">Syntax</span></span>  
  
```  
HRESULT OnSyncCallOut  
(  
    [in]  CALL_ID  in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*   out_pBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3eb7a-105">參數</span><span class="sxs-lookup"><span data-stu-id="3eb7a-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="3eb7a-106">[in]向外呼叫的識別碼。請參閱[CALL_ID 結構](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md)。</span><span class="sxs-lookup"><span data-stu-id="3eb7a-106">[in] ID of the call that is out. See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="3eb7a-107">[out]呼叫緩衝區。</span><span class="sxs-lookup"><span data-stu-id="3eb7a-107">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="3eb7a-108">[out]呼叫緩衝區，以位元組為單位的大小。</span><span class="sxs-lookup"><span data-stu-id="3eb7a-108">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3eb7a-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="3eb7a-109">Return Value</span></span>  
 <span data-ttu-id="3eb7a-110">如果此方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="3eb7a-110">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3eb7a-111">需求</span><span class="sxs-lookup"><span data-stu-id="3eb7a-111">Requirements</span></span>  
 <span data-ttu-id="3eb7a-112">**標頭：** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="3eb7a-112">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eb7a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3eb7a-113">See Also</span></span>  
 [<span data-ttu-id="3eb7a-114">INotifySink2 介面</span><span class="sxs-lookup"><span data-stu-id="3eb7a-114">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="3eb7a-115">INotifySource2 介面</span><span class="sxs-lookup"><span data-stu-id="3eb7a-115">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="3eb7a-116">INotifyConnection2 介面</span><span class="sxs-lookup"><span data-stu-id="3eb7a-116">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
