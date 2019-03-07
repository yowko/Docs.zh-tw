---
title: ICorDebugThread2::GetActiveFunctions 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetActiveFunctions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetActiveFunctions
helpviewer_keywords:
- GetActiveFunctions method [.NET Framework debugging]
- ICorDebugThread2::GetActiveFunctions method [.NET Framework debugging]
ms.assetid: 27fae01a-ecec-423a-973e-24f8de55826c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed13f78d5a1f6d54b12c86613715f4878a521bfa
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489926"
---
# <a name="icordebugthread2getactivefunctions-method"></a><span data-ttu-id="5ed77-102">ICorDebugThread2::GetActiveFunctions 方法</span><span class="sxs-lookup"><span data-stu-id="5ed77-102">ICorDebugThread2::GetActiveFunctions Method</span></span>
<span data-ttu-id="5ed77-103">在每個此執行緒的畫面格取得作用中的函式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5ed77-103">Gets information about the active function in each of this thread's frames.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ed77-104">語法</span><span class="sxs-lookup"><span data-stu-id="5ed77-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ed77-105">參數</span><span class="sxs-lookup"><span data-stu-id="5ed77-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="5ed77-106">[in] `pFunctions` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="5ed77-106">[in] The size of the `pFunctions` array.</span></span>  
  
 `pcFunctions`  
 <span data-ttu-id="5ed77-107">[out]中傳回的物件數目的指標`pFunctions`陣列。</span><span class="sxs-lookup"><span data-stu-id="5ed77-107">[out] A pointer to the number of objects returned in the `pFunctions` array.</span></span> <span data-ttu-id="5ed77-108">傳回的物件數目會等於受控框架在堆疊上的數字。</span><span class="sxs-lookup"><span data-stu-id="5ed77-108">The number of objects returned will be equal to the number of managed frames on the stack.</span></span>  
  
 `pFunctions`  
 <span data-ttu-id="5ed77-109">[in、 out]COR_ACTIVE_FUNCTION 物件陣列，其中每個包含此執行緒的框架中作用中的函式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5ed77-109">[in, out] An array of COR_ACTIVE_FUNCTION objects, each of which contains information about the active functions in this thread's frames.</span></span>  
  
 <span data-ttu-id="5ed77-110">第一個項目將用於分葉的框架，而且最後回到堆疊的根。</span><span class="sxs-lookup"><span data-stu-id="5ed77-110">The first element will be used for the leaf frame, and so on back to the root of the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ed77-111">備註</span><span class="sxs-lookup"><span data-stu-id="5ed77-111">Remarks</span></span>  
 <span data-ttu-id="5ed77-112">如果`pFunctions`為 null 輸入時，`GetActiveFunctions`傳回在堆疊上的函式的數目。</span><span class="sxs-lookup"><span data-stu-id="5ed77-112">If `pFunctions` is null on input, `GetActiveFunctions` returns only the number of functions that are on the stack.</span></span> <span data-ttu-id="5ed77-113">也就是說，如果`pFunctions`為 null 輸入時，`GetActiveFunctions`傳回值只能在`pcFunctions`。</span><span class="sxs-lookup"><span data-stu-id="5ed77-113">That is, If `pFunctions` is null on input, `GetActiveFunctions` returns a value only in `pcFunctions`.</span></span>  
  
 <span data-ttu-id="5ed77-114">`GetActiveFunctions`方法是做為最佳化透過從框架的堆疊追蹤，取得相同的資訊，因此包含原本 ICorDebugILFrame 物件為其完整的堆疊追蹤中的框架。</span><span class="sxs-lookup"><span data-stu-id="5ed77-114">The `GetActiveFunctions` method is intended as an optimization over getting the same information from frames in a stack trace, and includes only frames that would have had an ICorDebugILFrame object for them in the full stack trace.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ed77-115">需求</span><span class="sxs-lookup"><span data-stu-id="5ed77-115">Requirements</span></span>  
 <span data-ttu-id="5ed77-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5ed77-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ed77-117">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5ed77-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5ed77-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ed77-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ed77-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ed77-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
