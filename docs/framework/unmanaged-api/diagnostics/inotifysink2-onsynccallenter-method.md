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
ms.openlocfilehash: 78aaa5d8031e7b554eee2a147d9940ff8d7f7e02
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940383"
---
# <a name="inotifysink2onsynccallenter-method"></a><span data-ttu-id="20a32-102">INotifySink2::OnSyncCallEnter 方法</span><span class="sxs-lookup"><span data-stu-id="20a32-102">INotifySink2::OnSyncCallEnter Method</span></span>
<span data-ttu-id="20a32-103">取得叫用時進入呼叫。</span><span class="sxs-lookup"><span data-stu-id="20a32-103">Gets invoked when entering a call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20a32-104">語法</span><span class="sxs-lookup"><span data-stu-id="20a32-104">Syntax</span></span>  
  
```  
HRESULT OnSyncCallEnter  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20a32-105">參數</span><span class="sxs-lookup"><span data-stu-id="20a32-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="20a32-106">[in]呼叫輸入的識別碼。</span><span class="sxs-lookup"><span data-stu-id="20a32-106">[in] ID of the call being entered.</span></span> <span data-ttu-id="20a32-107">請參閱[CALL_ID 結構](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md)。</span><span class="sxs-lookup"><span data-stu-id="20a32-107">See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="20a32-108">[in]呼叫的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="20a32-108">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="20a32-109">[in]呼叫緩衝區，以位元組為單位的大小。</span><span class="sxs-lookup"><span data-stu-id="20a32-109">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20a32-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="20a32-110">Return Value</span></span>  
 <span data-ttu-id="20a32-111">如果方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="20a32-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20a32-112">需求</span><span class="sxs-lookup"><span data-stu-id="20a32-112">Requirements</span></span>  
 <span data-ttu-id="20a32-113">**標頭：** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="20a32-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20a32-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20a32-114">See also</span></span>

- [<span data-ttu-id="20a32-115">INotifySink2 介面</span><span class="sxs-lookup"><span data-stu-id="20a32-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="20a32-116">INotifySource2 介面</span><span class="sxs-lookup"><span data-stu-id="20a32-116">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="20a32-117">INotifyConnection2 介面</span><span class="sxs-lookup"><span data-stu-id="20a32-117">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
