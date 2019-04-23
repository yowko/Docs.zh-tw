---
title: INotifySink2::OnSyncCallReturn 方法
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallReturn
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallReturn
helpviewer_keywords:
- OnSyncCallReturn method [.NET Framework debugging]
- INotifySink2::OnSyncCallReturn method [.NET Framework debugging]
ms.assetid: c1bda761-6292-4750-a14b-7d5db8f33456
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0adc6ec1db3f12d1850bb6ff9a01d5b6cc5f90c7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157920"
---
# <a name="inotifysink2onsynccallreturn-method"></a><span data-ttu-id="5f5bf-102">INotifySink2::OnSyncCallReturn 方法</span><span class="sxs-lookup"><span data-stu-id="5f5bf-102">INotifySink2::OnSyncCallReturn Method</span></span>
<span data-ttu-id="5f5bf-103">取得叫用呼叫傳回時。</span><span class="sxs-lookup"><span data-stu-id="5f5bf-103">Gets invoked when a call returns.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f5bf-104">語法</span><span class="sxs-lookup"><span data-stu-id="5f5bf-104">Syntax</span></span>  
  
```  
HRESULT OnSyncCallReturn  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f5bf-105">參數</span><span class="sxs-lookup"><span data-stu-id="5f5bf-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="5f5bf-106">[in]從傳回的呼叫識別碼。</span><span class="sxs-lookup"><span data-stu-id="5f5bf-106">[in] ID of the call being returned from.</span></span> <span data-ttu-id="5f5bf-107">請參閱[CALL_ID 結構](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md)。</span><span class="sxs-lookup"><span data-stu-id="5f5bf-107">See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="5f5bf-108">[in]呼叫的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="5f5bf-108">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="5f5bf-109">[in]呼叫緩衝區，以位元組為單位的大小。</span><span class="sxs-lookup"><span data-stu-id="5f5bf-109">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5f5bf-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="5f5bf-110">Return Value</span></span>  
 <span data-ttu-id="5f5bf-111">如果方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="5f5bf-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f5bf-112">需求</span><span class="sxs-lookup"><span data-stu-id="5f5bf-112">Requirements</span></span>  
 <span data-ttu-id="5f5bf-113">**標頭：** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="5f5bf-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f5bf-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f5bf-114">See also</span></span>

- [<span data-ttu-id="5f5bf-115">INotifySink2 介面</span><span class="sxs-lookup"><span data-stu-id="5f5bf-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="5f5bf-116">INotifySource2 介面</span><span class="sxs-lookup"><span data-stu-id="5f5bf-116">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="5f5bf-117">INotifyConnection2 介面</span><span class="sxs-lookup"><span data-stu-id="5f5bf-117">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
