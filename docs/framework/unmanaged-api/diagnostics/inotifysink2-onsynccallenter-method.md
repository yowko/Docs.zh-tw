---
title: INotifySink2::OnSyncCallEnter 方法
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallEnter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallEnter
helpviewer_keywords:
- INotifySink2::OnSyncCallEnter method [.NET Framework debugging]
- OnSyncCallEnter method [.NET Framework debugging]
ms.assetid: e33265be-c25d-4145-ad02-c3e89d6f26c1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c44a150fa85ff0cbda4ff2b39acefb46045adad1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54500285"
---
# <a name="inotifysink2onsynccallenter-method"></a><span data-ttu-id="7c508-102">INotifySink2::OnSyncCallEnter 方法</span><span class="sxs-lookup"><span data-stu-id="7c508-102">INotifySink2::OnSyncCallEnter Method</span></span>
<span data-ttu-id="7c508-103">取得叫用時進入呼叫。</span><span class="sxs-lookup"><span data-stu-id="7c508-103">Gets invoked when entering a call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c508-104">語法</span><span class="sxs-lookup"><span data-stu-id="7c508-104">Syntax</span></span>  
  
```  
HRESULT OnSyncCallEnter  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7c508-105">參數</span><span class="sxs-lookup"><span data-stu-id="7c508-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="7c508-106">[in]呼叫輸入的識別碼。</span><span class="sxs-lookup"><span data-stu-id="7c508-106">[in] ID of the call being entered.</span></span> <span data-ttu-id="7c508-107">請參閱[CALL_ID 結構](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md)。</span><span class="sxs-lookup"><span data-stu-id="7c508-107">See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="7c508-108">[in]呼叫的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="7c508-108">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="7c508-109">[in]呼叫緩衝區，以位元組為單位的大小。</span><span class="sxs-lookup"><span data-stu-id="7c508-109">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7c508-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="7c508-110">Return Value</span></span>  
 <span data-ttu-id="7c508-111">如果方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="7c508-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c508-112">需求</span><span class="sxs-lookup"><span data-stu-id="7c508-112">Requirements</span></span>  
 <span data-ttu-id="7c508-113">**標頭：** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="7c508-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c508-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c508-114">See also</span></span>
- [<span data-ttu-id="7c508-115">INotifySink2 介面</span><span class="sxs-lookup"><span data-stu-id="7c508-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="7c508-116">INotifySource2 介面</span><span class="sxs-lookup"><span data-stu-id="7c508-116">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="7c508-117">INotifyConnection2 介面</span><span class="sxs-lookup"><span data-stu-id="7c508-117">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
