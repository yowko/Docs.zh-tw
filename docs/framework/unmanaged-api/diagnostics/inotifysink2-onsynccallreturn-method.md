---
title: "INotifySink2::OnSyncCallReturn 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: INotifySink2.OnSyncCallReturn
api_location: diasymreader.dll
api_type: COM
f1_keywords: INotifySink2::OnSyncCallReturn
helpviewer_keywords:
- OnSyncCallReturn method [.NET Framework debugging]
- INotifySink2::OnSyncCallReturn method [.NET Framework debugging]
ms.assetid: c1bda761-6292-4750-a14b-7d5db8f33456
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8f09d9ced41ecfe933a22ac41ee7f2065f1afcc6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="inotifysink2onsynccallreturn-method"></a><span data-ttu-id="83b62-102">INotifySink2::OnSyncCallReturn 方法</span><span class="sxs-lookup"><span data-stu-id="83b62-102">INotifySink2::OnSyncCallReturn Method</span></span>
<span data-ttu-id="83b62-103">取得叫用呼叫傳回時。</span><span class="sxs-lookup"><span data-stu-id="83b62-103">Gets invoked when a call returns.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83b62-104">語法</span><span class="sxs-lookup"><span data-stu-id="83b62-104">Syntax</span></span>  
  
```  
HRESULT OnSyncCallReturn  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83b62-105">參數</span><span class="sxs-lookup"><span data-stu-id="83b62-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="83b62-106">[in]呼叫傳回的識別碼。</span><span class="sxs-lookup"><span data-stu-id="83b62-106">[in] ID of the call being returned from.</span></span> <span data-ttu-id="83b62-107">請參閱[CALL_ID 結構](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md)。</span><span class="sxs-lookup"><span data-stu-id="83b62-107">See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="83b62-108">[in]呼叫緩衝區。</span><span class="sxs-lookup"><span data-stu-id="83b62-108">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="83b62-109">[in]呼叫緩衝區，以位元組為單位的大小。</span><span class="sxs-lookup"><span data-stu-id="83b62-109">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83b62-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="83b62-110">Return Value</span></span>  
 <span data-ttu-id="83b62-111">如果此方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="83b62-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83b62-112">需求</span><span class="sxs-lookup"><span data-stu-id="83b62-112">Requirements</span></span>  
 <span data-ttu-id="83b62-113">**標頭：** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="83b62-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83b62-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83b62-114">See Also</span></span>  
 [<span data-ttu-id="83b62-115">INotifySink2 介面</span><span class="sxs-lookup"><span data-stu-id="83b62-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="83b62-116">INotifySource2 介面</span><span class="sxs-lookup"><span data-stu-id="83b62-116">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="83b62-117">INotifyConnection2 介面</span><span class="sxs-lookup"><span data-stu-id="83b62-117">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
