---
title: INotifySink2::OnSyncCallOut 方法
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallOut
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallOut
helpviewer_keywords:
- INotifySink2::OnSyncCallOut method [.NET Framework debugging]
- OnSyncCallOut method [.NET Framework debugging]
ms.assetid: 97f15656-8677-4079-8553-a1d8603355d6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f4cea67587e4a33b4b9f8cbaa23cb7d299004a46
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736168"
---
# <a name="inotifysink2onsynccallout-method"></a><span data-ttu-id="d89f9-102">INotifySink2::OnSyncCallOut 方法</span><span class="sxs-lookup"><span data-stu-id="d89f9-102">INotifySink2::OnSyncCallOut Method</span></span>
<span data-ttu-id="d89f9-103">取得叫用時呼叫已推出。</span><span class="sxs-lookup"><span data-stu-id="d89f9-103">Gets invoked when a call is out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d89f9-104">語法</span><span class="sxs-lookup"><span data-stu-id="d89f9-104">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallOut  
(  
    [in]  CALL_ID  in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*   out_pBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d89f9-105">參數</span><span class="sxs-lookup"><span data-stu-id="d89f9-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="d89f9-106">[in]向外呼叫的 ID。請參閱[CALL_ID 結構](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md)。</span><span class="sxs-lookup"><span data-stu-id="d89f9-106">[in] ID of the call that is out. See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="d89f9-107">[out]呼叫的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="d89f9-107">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="d89f9-108">[out]呼叫緩衝區，以位元組為單位的大小。</span><span class="sxs-lookup"><span data-stu-id="d89f9-108">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d89f9-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="d89f9-109">Return Value</span></span>  
 <span data-ttu-id="d89f9-110">如果方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="d89f9-110">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d89f9-111">需求</span><span class="sxs-lookup"><span data-stu-id="d89f9-111">Requirements</span></span>  
 <span data-ttu-id="d89f9-112">**標頭：** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="d89f9-112">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d89f9-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d89f9-113">See also</span></span>

- [<span data-ttu-id="d89f9-114">INotifySink2 介面</span><span class="sxs-lookup"><span data-stu-id="d89f9-114">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="d89f9-115">INotifySource2 介面</span><span class="sxs-lookup"><span data-stu-id="d89f9-115">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="d89f9-116">INotifyConnection2 介面</span><span class="sxs-lookup"><span data-stu-id="d89f9-116">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
