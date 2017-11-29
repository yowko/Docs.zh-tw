---
title: "INotifySink2::OnSyncCallExit 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: INotifySink2.OnSyncCallExit
api_location: diasymreader.dll
api_type: COM
f1_keywords: INotifySink2::OnSyncCallExit
helpviewer_keywords:
- INotifySink2::OnSyncCallExit method [.NET Framework debugging]
- OnSyncCallExit method [.NET Framework debugging]
ms.assetid: d9d7600e-a8f5-443a-96de-67d26e130f2d
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8034717826316fe8ae4679c19e5002ca2c22c6fb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="inotifysink2onsynccallexit-method"></a><span data-ttu-id="b023e-102">INotifySink2::OnSyncCallExit 方法</span><span class="sxs-lookup"><span data-stu-id="b023e-102">INotifySink2::OnSyncCallExit Method</span></span>
<span data-ttu-id="b023e-103">結束呼叫時叫用。</span><span class="sxs-lookup"><span data-stu-id="b023e-103">Gets invoked when exiting a call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b023e-104">語法</span><span class="sxs-lookup"><span data-stu-id="b023e-104">Syntax</span></span>  
  
```  
HRESULT OnSyncCallExit  
(  
    [in]  CALL_ID   in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*    out_pBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b023e-105">參數</span><span class="sxs-lookup"><span data-stu-id="b023e-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="b023e-106">[in]正在結束呼叫的識別碼。</span><span class="sxs-lookup"><span data-stu-id="b023e-106">[in] ID of the call being exited.</span></span> <span data-ttu-id="b023e-107">請參閱[CALL_ID 結構](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md)。</span><span class="sxs-lookup"><span data-stu-id="b023e-107">See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="b023e-108">[out]呼叫緩衝區。</span><span class="sxs-lookup"><span data-stu-id="b023e-108">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="b023e-109">[out]呼叫緩衝區，以位元組為單位的大小。</span><span class="sxs-lookup"><span data-stu-id="b023e-109">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b023e-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="b023e-110">Return Value</span></span>  
 <span data-ttu-id="b023e-111">如果此方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="b023e-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b023e-112">需求</span><span class="sxs-lookup"><span data-stu-id="b023e-112">Requirements</span></span>  
 <span data-ttu-id="b023e-113">**標頭：** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="b023e-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b023e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b023e-114">See Also</span></span>  
 [<span data-ttu-id="b023e-115">INotifySink2 介面</span><span class="sxs-lookup"><span data-stu-id="b023e-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="b023e-116">INotifySource2 介面</span><span class="sxs-lookup"><span data-stu-id="b023e-116">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="b023e-117">INotifyConnection2 介面</span><span class="sxs-lookup"><span data-stu-id="b023e-117">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
