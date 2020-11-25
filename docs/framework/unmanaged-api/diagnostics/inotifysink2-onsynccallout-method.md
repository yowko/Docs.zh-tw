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
ms.openlocfilehash: 00f6032f41caf54d7366de30a449f1ae76e8bbd0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719979"
---
# <a name="inotifysink2onsynccallout-method"></a><span data-ttu-id="7ad07-102">INotifySink2::OnSyncCallOut 方法</span><span class="sxs-lookup"><span data-stu-id="7ad07-102">INotifySink2::OnSyncCallOut Method</span></span>

<span data-ttu-id="7ad07-103">在呼叫超時時叫用。</span><span class="sxs-lookup"><span data-stu-id="7ad07-103">Gets invoked when a call is out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ad07-104">語法</span><span class="sxs-lookup"><span data-stu-id="7ad07-104">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallOut  
(  
    [in]  CALL_ID  in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*   out_pBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ad07-105">參數</span><span class="sxs-lookup"><span data-stu-id="7ad07-105">Parameters</span></span>  

 `in_CallID`  
 <span data-ttu-id="7ad07-106">在輸出的呼叫識別碼。請參閱 [CALL_ID 結構](call-id-structure.md)。</span><span class="sxs-lookup"><span data-stu-id="7ad07-106">[in] ID of the call that is out. See [CALL_ID Structure](call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="7ad07-107">擴展呼叫緩衝區。</span><span class="sxs-lookup"><span data-stu-id="7ad07-107">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="7ad07-108">擴展呼叫緩衝區的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="7ad07-108">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7ad07-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="7ad07-109">Return Value</span></span>  

 <span data-ttu-id="7ad07-110">如果方法成功，則為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="7ad07-110">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ad07-111">需求</span><span class="sxs-lookup"><span data-stu-id="7ad07-111">Requirements</span></span>  

 <span data-ttu-id="7ad07-112">**標頭：** ProtocolNotify2 .idl</span><span class="sxs-lookup"><span data-stu-id="7ad07-112">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ad07-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ad07-113">See also</span></span>

- [<span data-ttu-id="7ad07-114">INotifySink2 介面</span><span class="sxs-lookup"><span data-stu-id="7ad07-114">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="7ad07-115">INotifySource2 介面</span><span class="sxs-lookup"><span data-stu-id="7ad07-115">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="7ad07-116">INotifyConnection2 介面</span><span class="sxs-lookup"><span data-stu-id="7ad07-116">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
