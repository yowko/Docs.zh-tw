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
ms.openlocfilehash: ff1dabcfc366607639cd98be4392f8dd59dc83a1
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442003"
---
# <a name="inotifysink2onsynccallreturn-method"></a><span data-ttu-id="e8baa-102">INotifySink2::OnSyncCallReturn 方法</span><span class="sxs-lookup"><span data-stu-id="e8baa-102">INotifySink2::OnSyncCallReturn Method</span></span>
<span data-ttu-id="e8baa-103">當呼叫傳回時，就會叫用。</span><span class="sxs-lookup"><span data-stu-id="e8baa-103">Gets invoked when a call returns.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8baa-104">語法</span><span class="sxs-lookup"><span data-stu-id="e8baa-104">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallReturn  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8baa-105">參數</span><span class="sxs-lookup"><span data-stu-id="e8baa-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="e8baa-106">在從傳回的呼叫識別碼。</span><span class="sxs-lookup"><span data-stu-id="e8baa-106">[in] ID of the call being returned from.</span></span> <span data-ttu-id="e8baa-107">請參閱[CALL_ID 結構](call-id-structure.md)。</span><span class="sxs-lookup"><span data-stu-id="e8baa-107">See [CALL_ID Structure](call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="e8baa-108">在呼叫緩衝區。</span><span class="sxs-lookup"><span data-stu-id="e8baa-108">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="e8baa-109">在呼叫緩衝區的大小，以位元組為單位。</span><span class="sxs-lookup"><span data-stu-id="e8baa-109">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8baa-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="e8baa-110">Return Value</span></span>  
 <span data-ttu-id="e8baa-111">如果方法成功，則 S_OK。</span><span class="sxs-lookup"><span data-stu-id="e8baa-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8baa-112">需求</span><span class="sxs-lookup"><span data-stu-id="e8baa-112">Requirements</span></span>  
 <span data-ttu-id="e8baa-113">**標頭：** ProtocolNotify2 .idl</span><span class="sxs-lookup"><span data-stu-id="e8baa-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8baa-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8baa-114">See also</span></span>

- [<span data-ttu-id="e8baa-115">INotifySink2 介面</span><span class="sxs-lookup"><span data-stu-id="e8baa-115">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="e8baa-116">INotifySource2 介面</span><span class="sxs-lookup"><span data-stu-id="e8baa-116">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="e8baa-117">INotifyConnection2 介面</span><span class="sxs-lookup"><span data-stu-id="e8baa-117">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
