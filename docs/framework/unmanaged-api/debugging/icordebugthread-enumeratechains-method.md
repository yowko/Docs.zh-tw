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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f131f7566376d6474f3189d5eb612b30bec2e2b7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648428"
---
# <a name="icordebugthreadenumeratechains-method"></a><span data-ttu-id="f5161-102">ICorDebugThread::EnumerateChains 方法</span><span class="sxs-lookup"><span data-stu-id="f5161-102">ICorDebugThread::EnumerateChains Method</span></span>
<span data-ttu-id="f5161-103">ICorDebugChainEnum 列舉值，其中包含這個 ICorDebugThread 物件中的所有堆疊鏈結中取得的介面指標。</span><span class="sxs-lookup"><span data-stu-id="f5161-103">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5161-104">語法</span><span class="sxs-lookup"><span data-stu-id="f5161-104">Syntax</span></span>  
  
```  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5161-105">參數</span><span class="sxs-lookup"><span data-stu-id="f5161-105">Parameters</span></span>  
 `ppChains`  
 <span data-ttu-id="f5161-106">[out]位址指標`ICorDebugChainEnum`這個執行緒，開始使用 （也就是最新的） 鏈結中的鏈結，這個物件可讓所有堆疊的列舉型別。</span><span class="sxs-lookup"><span data-stu-id="f5161-106">[out] A pointer to the address of an `ICorDebugChainEnum` object that allows enumeration of all the stack chains in this thread, starting at the active (that is, the most recent) chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5161-107">備註</span><span class="sxs-lookup"><span data-stu-id="f5161-107">Remarks</span></span>  
 <span data-ttu-id="f5161-108">堆疊鏈結代表執行緒的實體呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="f5161-108">The stack chain represents the physical call stack for the thread.</span></span> <span data-ttu-id="f5161-109">在下列情況下建立堆疊鏈結界限：</span><span class="sxs-lookup"><span data-stu-id="f5161-109">The following circumstances create a stack chain boundary:</span></span>  
  
- <span data-ttu-id="f5161-110">在 managed 至 unmanaged 或非受控--受管理的轉換。</span><span class="sxs-lookup"><span data-stu-id="f5161-110">A managed-to-unmanaged or unmanaged-to-managed transition.</span></span>  
  
- <span data-ttu-id="f5161-111">內容切換。</span><span class="sxs-lookup"><span data-stu-id="f5161-111">A context switch.</span></span>  
  
- <span data-ttu-id="f5161-112">偵錯工具攔截使用者往來文章。</span><span class="sxs-lookup"><span data-stu-id="f5161-112">A debugger hijacking of a user thread.</span></span>  
  
 <span data-ttu-id="f5161-113">在單一的內容中執行純粹是 managed 程式碼的執行緒簡單案例中，執行緒和堆疊鏈結之間會有一對一的對應關係。</span><span class="sxs-lookup"><span data-stu-id="f5161-113">In the simple case for a thread that is running purely managed code in a single context, a one-to-one correspondence will exist between threads and stack chains.</span></span>  
  
 <span data-ttu-id="f5161-114">偵錯工具可能想要重新排列成邏輯呼叫堆疊的所有執行緒的實體呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="f5161-114">A debugger may want to rearrange the physical call stacks of all threads into logical call stacks.</span></span> <span data-ttu-id="f5161-115">這會牽涉到排序依據其呼叫端/被呼叫端的關聯性的所有執行緒的鏈結，並且重新分組。</span><span class="sxs-lookup"><span data-stu-id="f5161-115">This would involve sorting all the threads' chains by their caller/callee relationships and regrouping them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5161-116">需求</span><span class="sxs-lookup"><span data-stu-id="f5161-116">Requirements</span></span>  
 <span data-ttu-id="f5161-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f5161-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5161-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f5161-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5161-119">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5161-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5161-120">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5161-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
