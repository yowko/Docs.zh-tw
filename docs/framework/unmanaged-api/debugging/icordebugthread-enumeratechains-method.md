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
ms.openlocfilehash: 76b231f00651186518d3bccfafa5780f258c4f75
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688181"
---
# <a name="icordebugthreadenumeratechains-method"></a><span data-ttu-id="ad347-102">ICorDebugThread::EnumerateChains 方法</span><span class="sxs-lookup"><span data-stu-id="ad347-102">ICorDebugThread::EnumerateChains Method</span></span>

<span data-ttu-id="ad347-103">取得 ICorDebugChainEnum 列舉值的介面指標，其中包含這個 ICorDebugThread 物件中的所有堆疊鏈。</span><span class="sxs-lookup"><span data-stu-id="ad347-103">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad347-104">語法</span><span class="sxs-lookup"><span data-stu-id="ad347-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad347-105">參數</span><span class="sxs-lookup"><span data-stu-id="ad347-105">Parameters</span></span>  

 `ppChains`  
 <span data-ttu-id="ad347-106">擴展物件位址的指標， `ICorDebugChainEnum` 該物件允許列舉這個執行緒中所有堆疊鏈的，從作用中的 (開始，也就是最新的) 鏈。</span><span class="sxs-lookup"><span data-stu-id="ad347-106">[out] A pointer to the address of an `ICorDebugChainEnum` object that allows enumeration of all the stack chains in this thread, starting at the active (that is, the most recent) chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad347-107">備註</span><span class="sxs-lookup"><span data-stu-id="ad347-107">Remarks</span></span>  

 <span data-ttu-id="ad347-108">堆疊鏈表示執行緒的實體呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="ad347-108">The stack chain represents the physical call stack for the thread.</span></span> <span data-ttu-id="ad347-109">下列情況會建立堆疊鏈界限：</span><span class="sxs-lookup"><span data-stu-id="ad347-109">The following circumstances create a stack chain boundary:</span></span>  
  
- <span data-ttu-id="ad347-110">受控對非受控或非受控對管理的轉換。</span><span class="sxs-lookup"><span data-stu-id="ad347-110">A managed-to-unmanaged or unmanaged-to-managed transition.</span></span>  
  
- <span data-ttu-id="ad347-111">內容切換。</span><span class="sxs-lookup"><span data-stu-id="ad347-111">A context switch.</span></span>  
  
- <span data-ttu-id="ad347-112">使用者執行緒的偵錯工具劫持。</span><span class="sxs-lookup"><span data-stu-id="ad347-112">A debugger hijacking of a user thread.</span></span>  
  
 <span data-ttu-id="ad347-113">在單一內容中執行單純 managed 程式碼的執行緒的簡單案例中，會線上程與堆疊鏈之間存在一對一的對應。</span><span class="sxs-lookup"><span data-stu-id="ad347-113">In the simple case for a thread that is running purely managed code in a single context, a one-to-one correspondence will exist between threads and stack chains.</span></span>  
  
 <span data-ttu-id="ad347-114">偵錯工具可能會想要將所有線程的實體呼叫堆疊重新排列成邏輯呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="ad347-114">A debugger may want to rearrange the physical call stacks of all threads into logical call stacks.</span></span> <span data-ttu-id="ad347-115">這會牽涉到依呼叫端/被呼叫端關聯性排序所有線程的鏈，並加以 regrouping。</span><span class="sxs-lookup"><span data-stu-id="ad347-115">This would involve sorting all the threads' chains by their caller/callee relationships and regrouping them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad347-116">需求</span><span class="sxs-lookup"><span data-stu-id="ad347-116">Requirements</span></span>  

 <span data-ttu-id="ad347-117">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ad347-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad347-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad347-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad347-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad347-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad347-120">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad347-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
