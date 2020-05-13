---
title: ICorDebugThread::EnumerateChains 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.EnumerateChains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::EnumerateChains
helpviewer_keywords:
- EnumerateChains method [.NET Framework debugging]
- ICorDebugThread::EnumerateChains method [.NET Framework debugging]
ms.assetid: ec00bc21-117e-4acd-9301-2cfafd5be8d3
topic_type:
- apiref
ms.openlocfilehash: 711fccd65379bc3e5e178869e7220dd84fd07fbe
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379708"
---
# <a name="icordebugthreadenumeratechains-method"></a><span data-ttu-id="178f0-102">ICorDebugThread::EnumerateChains 方法</span><span class="sxs-lookup"><span data-stu-id="178f0-102">ICorDebugThread::EnumerateChains Method</span></span>
<span data-ttu-id="178f0-103">取得 ICorDebugChainEnum 列舉值的介面指標，其中包含這個 ICorDebugThread 物件中的所有堆疊鏈。</span><span class="sxs-lookup"><span data-stu-id="178f0-103">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="178f0-104">語法</span><span class="sxs-lookup"><span data-stu-id="178f0-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="178f0-105">參數</span><span class="sxs-lookup"><span data-stu-id="178f0-105">Parameters</span></span>  
 `ppChains`  
 <span data-ttu-id="178f0-106">脫銷物件位址的指標 `ICorDebugChainEnum` ，允許在此執行緒中列舉所有堆疊鏈，從作用中（也就是最新的）鏈開始。</span><span class="sxs-lookup"><span data-stu-id="178f0-106">[out] A pointer to the address of an `ICorDebugChainEnum` object that allows enumeration of all the stack chains in this thread, starting at the active (that is, the most recent) chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="178f0-107">備註</span><span class="sxs-lookup"><span data-stu-id="178f0-107">Remarks</span></span>  
 <span data-ttu-id="178f0-108">堆疊鏈代表執行緒的實體呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="178f0-108">The stack chain represents the physical call stack for the thread.</span></span> <span data-ttu-id="178f0-109">下列情況會建立堆疊鏈界限：</span><span class="sxs-lookup"><span data-stu-id="178f0-109">The following circumstances create a stack chain boundary:</span></span>  
  
- <span data-ttu-id="178f0-110">受控對非受控或未受管理的轉換。</span><span class="sxs-lookup"><span data-stu-id="178f0-110">A managed-to-unmanaged or unmanaged-to-managed transition.</span></span>  
  
- <span data-ttu-id="178f0-111">內容切換。</span><span class="sxs-lookup"><span data-stu-id="178f0-111">A context switch.</span></span>  
  
- <span data-ttu-id="178f0-112">使用者執行緒的偵錯工具劫持。</span><span class="sxs-lookup"><span data-stu-id="178f0-112">A debugger hijacking of a user thread.</span></span>  
  
 <span data-ttu-id="178f0-113">在簡單的案例中，如果是在單一內容中執行純粹受控程式碼的執行緒，則執行緒與堆疊鏈之間會有一對一的對應關係。</span><span class="sxs-lookup"><span data-stu-id="178f0-113">In the simple case for a thread that is running purely managed code in a single context, a one-to-one correspondence will exist between threads and stack chains.</span></span>  
  
 <span data-ttu-id="178f0-114">偵錯工具可能會想要將所有線程的實體呼叫堆疊重新排列為邏輯呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="178f0-114">A debugger may want to rearrange the physical call stacks of all threads into logical call stacks.</span></span> <span data-ttu-id="178f0-115">這牽涉到以呼叫端/被呼叫端的關聯性來排序所有線程的鏈，並加以 regrouping。</span><span class="sxs-lookup"><span data-stu-id="178f0-115">This would involve sorting all the threads' chains by their caller/callee relationships and regrouping them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="178f0-116">需求</span><span class="sxs-lookup"><span data-stu-id="178f0-116">Requirements</span></span>  
 <span data-ttu-id="178f0-117">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="178f0-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="178f0-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="178f0-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="178f0-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="178f0-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="178f0-120">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="178f0-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
