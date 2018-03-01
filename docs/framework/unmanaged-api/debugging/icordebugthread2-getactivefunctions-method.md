---
title: "ICorDebugThread2::GetActiveFunctions 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ecd9446f642011b21f784019f583f49e3a70433a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread2getactivefunctions-method"></a><span data-ttu-id="8d426-102">ICorDebugThread2::GetActiveFunctions 方法</span><span class="sxs-lookup"><span data-stu-id="8d426-102">ICorDebugThread2::GetActiveFunctions Method</span></span>
<span data-ttu-id="8d426-103">在每個執行緒框架中取得作用中的函式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8d426-103">Gets information about the active function in each of this thread's frames.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d426-104">語法</span><span class="sxs-lookup"><span data-stu-id="8d426-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8d426-105">參數</span><span class="sxs-lookup"><span data-stu-id="8d426-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="8d426-106">[in] `pFunctions` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="8d426-106">[in] The size of the `pFunctions` array.</span></span>  
  
 `pcFunctions`  
 <span data-ttu-id="8d426-107">[out]傳回的物件數目的指標`pFunctions`陣列。</span><span class="sxs-lookup"><span data-stu-id="8d426-107">[out] A pointer to the number of objects returned in the `pFunctions` array.</span></span> <span data-ttu-id="8d426-108">傳回的物件數目會等於 managed 堆疊框架數目。</span><span class="sxs-lookup"><span data-stu-id="8d426-108">The number of objects returned will be equal to the number of managed frames on the stack.</span></span>  
  
 `pFunctions`  
 <span data-ttu-id="8d426-109">[in、 out]COR_ACTIVE_FUNCTION 物件陣列，其中每一個都包含在這個執行緒框架中作用中的函式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8d426-109">[in, out] An array of COR_ACTIVE_FUNCTION objects, each of which contains information about the active functions in this thread's frames.</span></span>  
  
 <span data-ttu-id="8d426-110">第一個項目將用於分葉框架和堆疊的根目錄等等上一步。</span><span class="sxs-lookup"><span data-stu-id="8d426-110">The first element will be used for the leaf frame, and so on back to the root of the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d426-111">備註</span><span class="sxs-lookup"><span data-stu-id="8d426-111">Remarks</span></span>  
 <span data-ttu-id="8d426-112">如果`pFunctions`為輸入時，null`GetActiveFunctions`傳回在堆疊上的函式的數目。</span><span class="sxs-lookup"><span data-stu-id="8d426-112">If `pFunctions` is null on input, `GetActiveFunctions` returns only the number of functions that are on the stack.</span></span> <span data-ttu-id="8d426-113">也就是說，如果`pFunctions`為輸入時，null`GetActiveFunctions`傳回值，僅在`pcFunctions`。</span><span class="sxs-lookup"><span data-stu-id="8d426-113">That is, If `pFunctions` is null on input, `GetActiveFunctions` returns a value only in `pcFunctions`.</span></span>  
  
 <span data-ttu-id="8d426-114">`GetActiveFunctions`方法主要為了最佳化透過由框架的堆疊追蹤取得相同的資訊並包含原本 ICorDebugILFrame 物件為其完整的堆疊追蹤中的框架。</span><span class="sxs-lookup"><span data-stu-id="8d426-114">The `GetActiveFunctions` method is intended as an optimization over getting the same information from frames in a stack trace, and includes only frames that would have had an ICorDebugILFrame object for them in the full stack trace.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d426-115">需求</span><span class="sxs-lookup"><span data-stu-id="8d426-115">Requirements</span></span>  
 <span data-ttu-id="8d426-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8d426-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d426-117">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8d426-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d426-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d426-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d426-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d426-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
