---
title: "ICorDebugThread::EnumerateChains 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.EnumerateChains
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::EnumerateChains
helpviewer_keywords:
- EnumerateChains method [.NET Framework debugging]
- ICorDebugThread::EnumerateChains method [.NET Framework debugging]
ms.assetid: ec00bc21-117e-4acd-9301-2cfafd5be8d3
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 67b5a5da0a0053536ab4331e9d134464a4330500
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadenumeratechains-method"></a><span data-ttu-id="22d5c-102">ICorDebugThread::EnumerateChains 方法</span><span class="sxs-lookup"><span data-stu-id="22d5c-102">ICorDebugThread::EnumerateChains Method</span></span>
<span data-ttu-id="22d5c-103">ICorDebugChainEnum 列舉值，其中包含這個 ICorDebugThread 物件中的所有堆疊鏈結中取得的介面指標。</span><span class="sxs-lookup"><span data-stu-id="22d5c-103">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22d5c-104">語法</span><span class="sxs-lookup"><span data-stu-id="22d5c-104">Syntax</span></span>  
  
```  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="22d5c-105">參數</span><span class="sxs-lookup"><span data-stu-id="22d5c-105">Parameters</span></span>  
 `ppChains`  
 <span data-ttu-id="22d5c-106">[out]位址指標`ICorDebugChainEnum`鏈結這個執行緒開始作用中 （也就是最新的） 鏈結中的物件，可讓所有堆疊的列舉。</span><span class="sxs-lookup"><span data-stu-id="22d5c-106">[out] A pointer to the address of an `ICorDebugChainEnum` object that allows enumeration of all the stack chains in this thread, starting at the active (that is, the most recent) chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22d5c-107">備註</span><span class="sxs-lookup"><span data-stu-id="22d5c-107">Remarks</span></span>  
 <span data-ttu-id="22d5c-108">堆疊鏈結代表執行緒的實際呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="22d5c-108">The stack chain represents the physical call stack for the thread.</span></span> <span data-ttu-id="22d5c-109">在下列情況下建立堆疊鏈結界限：</span><span class="sxs-lookup"><span data-stu-id="22d5c-109">The following circumstances create a stack chain boundary:</span></span>  
  
-   <span data-ttu-id="22d5c-110">管理至 unmanaged 或 unmanaged--受管理的轉換。</span><span class="sxs-lookup"><span data-stu-id="22d5c-110">A managed-to-unmanaged or unmanaged-to-managed transition.</span></span>  
  
-   <span data-ttu-id="22d5c-111">內容切換。</span><span class="sxs-lookup"><span data-stu-id="22d5c-111">A context switch.</span></span>  
  
-   <span data-ttu-id="22d5c-112">A 劫持使用者執行緒偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="22d5c-112">A debugger hijacking of a user thread.</span></span>  
  
 <span data-ttu-id="22d5c-113">簡單案例中的單一內容中執行純粹是 managed 程式碼的執行緒，執行緒與堆疊鏈結之間會有一對一的對應。</span><span class="sxs-lookup"><span data-stu-id="22d5c-113">In the simple case for a thread that is running purely managed code in a single context, a one-to-one correspondence will exist between threads and stack chains.</span></span>  
  
 <span data-ttu-id="22d5c-114">偵錯工具可能想要重新排列成邏輯呼叫堆疊的所有執行緒的實際呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="22d5c-114">A debugger may want to rearrange the physical call stacks of all threads into logical call stacks.</span></span> <span data-ttu-id="22d5c-115">這會牽涉到排序依據其呼叫端/被呼叫端的關聯性的所有執行緒的鏈結，並且重新分組。</span><span class="sxs-lookup"><span data-stu-id="22d5c-115">This would involve sorting all the threads' chains by their caller/callee relationships and regrouping them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22d5c-116">需求</span><span class="sxs-lookup"><span data-stu-id="22d5c-116">Requirements</span></span>  
 <span data-ttu-id="22d5c-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="22d5c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22d5c-118">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="22d5c-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="22d5c-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22d5c-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22d5c-120">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22d5c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
