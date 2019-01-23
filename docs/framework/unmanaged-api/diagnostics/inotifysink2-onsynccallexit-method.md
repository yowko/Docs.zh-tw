---
title: INotifySink2::OnSyncCallExit 方法
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallExit
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallExit
helpviewer_keywords:
- INotifySink2::OnSyncCallExit method [.NET Framework debugging]
- OnSyncCallExit method [.NET Framework debugging]
ms.assetid: d9d7600e-a8f5-443a-96de-67d26e130f2d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9cff5d2dd2cf13e8626d1cca7f66c976dad6d90f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620915"
---
# <a name="inotifysink2onsynccallexit-method"></a><span data-ttu-id="f08aa-102">INotifySink2::OnSyncCallExit 方法</span><span class="sxs-lookup"><span data-stu-id="f08aa-102">INotifySink2::OnSyncCallExit Method</span></span>
<span data-ttu-id="f08aa-103">結束呼叫時叫用。</span><span class="sxs-lookup"><span data-stu-id="f08aa-103">Gets invoked when exiting a call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f08aa-104">語法</span><span class="sxs-lookup"><span data-stu-id="f08aa-104">Syntax</span></span>  
  
```  
HRESULT OnSyncCallExit  
(  
    [in]  CALL_ID   in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*    out_pBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f08aa-105">參數</span><span class="sxs-lookup"><span data-stu-id="f08aa-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="f08aa-106">[in]正在結束的呼叫識別碼。</span><span class="sxs-lookup"><span data-stu-id="f08aa-106">[in] ID of the call being exited.</span></span> <span data-ttu-id="f08aa-107">請參閱[CALL_ID 結構](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md)。</span><span class="sxs-lookup"><span data-stu-id="f08aa-107">See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="f08aa-108">[out]呼叫的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f08aa-108">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="f08aa-109">[out]呼叫緩衝區，以位元組為單位的大小。</span><span class="sxs-lookup"><span data-stu-id="f08aa-109">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f08aa-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="f08aa-110">Return Value</span></span>  
 <span data-ttu-id="f08aa-111">如果方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="f08aa-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f08aa-112">需求</span><span class="sxs-lookup"><span data-stu-id="f08aa-112">Requirements</span></span>  
 <span data-ttu-id="f08aa-113">**標頭：** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="f08aa-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f08aa-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f08aa-114">See also</span></span>
- [<span data-ttu-id="f08aa-115">INotifySink2 介面</span><span class="sxs-lookup"><span data-stu-id="f08aa-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="f08aa-116">INotifySource2 介面</span><span class="sxs-lookup"><span data-stu-id="f08aa-116">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="f08aa-117">INotifyConnection2 介面</span><span class="sxs-lookup"><span data-stu-id="f08aa-117">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
