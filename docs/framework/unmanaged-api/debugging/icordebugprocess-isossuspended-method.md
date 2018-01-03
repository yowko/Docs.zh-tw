---
title: "ICorDebugProcess::IsOSSuspended 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.IsOSSuspended
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::IsOSSuspended
helpviewer_keywords:
- IsOSSuspended method [.NET Framework debugging]
- ICorDebugProcess::IsOSSuspended method [.NET Framework debugging]
ms.assetid: 83406cb2-5797-4402-872d-89c9516aefec
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 97c394e3084007227cf157c62a12df3f5cfac8e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessisossuspended-method"></a><span data-ttu-id="1c034-102">ICorDebugProcess::IsOSSuspended 方法</span><span class="sxs-lookup"><span data-stu-id="1c034-102">ICorDebugProcess::IsOSSuspended Method</span></span>
<span data-ttu-id="1c034-103">取得值，指出指定的執行緒是否已暫止偵錯工具停止此處理序的結果。</span><span class="sxs-lookup"><span data-stu-id="1c034-103">Gets a value that indicates whether the specified thread has been suspended as a result of the debugger stopping this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c034-104">語法</span><span class="sxs-lookup"><span data-stu-id="1c034-104">Syntax</span></span>  
  
```  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1c034-105">參數</span><span class="sxs-lookup"><span data-stu-id="1c034-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="1c034-106">[in]有問題的執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="1c034-106">[in] The ID of thread in question.</span></span>  
  
 `pbSuspended`  
 <span data-ttu-id="1c034-107">[out]為的布林值的指標`true`如果指定的執行緒已經暫止的; 否則為 *`pbSuspended`是`false`。</span><span class="sxs-lookup"><span data-stu-id="1c034-107">[out] A pointer to a Boolean value that is `true` if the specified thread has been suspended; otherwise *`pbSuspended` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c034-108">備註</span><span class="sxs-lookup"><span data-stu-id="1c034-108">Remarks</span></span>  
 <span data-ttu-id="1c034-109">指定的執行緒的 Win32 時指定的執行緒已暫停偵錯工具停止此處理序的結果，暫停計數就會累加 1。</span><span class="sxs-lookup"><span data-stu-id="1c034-109">When the specified thread has been suspended as a result of the debugger stopping this process, the specified thread's Win32 suspend count is incremented by one.</span></span> <span data-ttu-id="1c034-110">偵錯工具使用者介面 (UI) 可能會想要取得這項資訊納入考量，如果它顯示作業系統 (OS) 暫停的使用者執行緒計數。</span><span class="sxs-lookup"><span data-stu-id="1c034-110">The debugger user interface (UI) may want to take this information into account if it displays the operating system (OS) suspend count of the thread to the user.</span></span>  
  
 <span data-ttu-id="1c034-111">`IsOSSuspended`方法有意義的 unmanaged 偵錯內容中。</span><span class="sxs-lookup"><span data-stu-id="1c034-111">The `IsOSSuspended` method makes sense only in the context of unmanaged debugging.</span></span> <span data-ttu-id="1c034-112">Managed 偵錯期間，執行緒會以合作方式暫止，而非 OS 暫停。</span><span class="sxs-lookup"><span data-stu-id="1c034-112">During managed debugging, threads are cooperatively suspended rather than OS-suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c034-113">需求</span><span class="sxs-lookup"><span data-stu-id="1c034-113">Requirements</span></span>  
 <span data-ttu-id="1c034-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1c034-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c034-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1c034-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c034-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c034-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c034-117">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c034-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
