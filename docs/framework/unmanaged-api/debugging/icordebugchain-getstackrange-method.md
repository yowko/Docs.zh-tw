---
title: ICorDebugChain::GetStackRange 方法
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetStackRange
helpviewer_keywords:
- ICorDebugChain::GetStackRange method [.NET Framework debugging]
- GetStackRange method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 554284e7-3f6c-4d40-8da5-1c9317fbd484
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac40927ac9469e4a2fb74fb550287130b9bb9f83
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989452"
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="6d54b-102">ICorDebugChain::GetStackRange 方法</span><span class="sxs-lookup"><span data-stu-id="6d54b-102">ICorDebugChain::GetStackRange Method</span></span>
<span data-ttu-id="6d54b-103">取得這個鏈結的堆疊區段的位址範圍。</span><span class="sxs-lookup"><span data-stu-id="6d54b-103">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d54b-104">語法</span><span class="sxs-lookup"><span data-stu-id="6d54b-104">Syntax</span></span>  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d54b-105">參數</span><span class="sxs-lookup"><span data-stu-id="6d54b-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="6d54b-106">[out]指標`CORDB_ADDRESS`是堆疊區段的起始位址的值。</span><span class="sxs-lookup"><span data-stu-id="6d54b-106">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="6d54b-107">[out]指標`CORDB_ADDRESS`是堆疊區段的結束位址的值。</span><span class="sxs-lookup"><span data-stu-id="6d54b-107">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d54b-108">備註</span><span class="sxs-lookup"><span data-stu-id="6d54b-108">Remarks</span></span>  
 <span data-ttu-id="6d54b-109">數值範圍是僅對比較的堆疊框架位置有意義的。</span><span class="sxs-lookup"><span data-stu-id="6d54b-109">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="6d54b-110">您不能做出任何假設項目實際上儲存在堆疊上。</span><span class="sxs-lookup"><span data-stu-id="6d54b-110">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d54b-111">需求</span><span class="sxs-lookup"><span data-stu-id="6d54b-111">Requirements</span></span>  
 <span data-ttu-id="6d54b-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6d54b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d54b-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d54b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d54b-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d54b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d54b-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d54b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
