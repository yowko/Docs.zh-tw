---
title: ICorDebugFrame::GetStackRange 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetStackRange
helpviewer_keywords:
- GetStackRange method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetStackRange method [.NET Framework debugging]
ms.assetid: fab037cb-fda6-40fb-9367-921e435dd5a0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 43532888d181adcb7a7e3760f2a5e3d8f664a35c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995809"
---
# <a name="icordebugframegetstackrange-method"></a><span data-ttu-id="26b59-102">ICorDebugFrame::GetStackRange 方法</span><span class="sxs-lookup"><span data-stu-id="26b59-102">ICorDebugFrame::GetStackRange Method</span></span>
<span data-ttu-id="26b59-103">取得此堆疊框架的絕對位址範圍。</span><span class="sxs-lookup"><span data-stu-id="26b59-103">Gets the absolute address range of this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26b59-104">語法</span><span class="sxs-lookup"><span data-stu-id="26b59-104">Syntax</span></span>  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26b59-105">參數</span><span class="sxs-lookup"><span data-stu-id="26b59-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="26b59-106">[out]指標`CORDB_ADDRESS`，指定所表示的堆疊框架的起始位址`ICorDebugFrame`物件。</span><span class="sxs-lookup"><span data-stu-id="26b59-106">[out] A pointer to a `CORDB_ADDRESS` that specifies the starting address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="26b59-107">[out]指標`CORDB_ADDRESS`，指定所表示的堆疊框架的結束位址`ICorDebugFrame`物件。</span><span class="sxs-lookup"><span data-stu-id="26b59-107">[out] A pointer to a `CORDB_ADDRESS` that specifies the ending address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26b59-108">備註</span><span class="sxs-lookup"><span data-stu-id="26b59-108">Remarks</span></span>  
 <span data-ttu-id="26b59-109">在堆疊的位址範圍可用於拼湊從多個偵錯引擎收集的交錯的堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="26b59-109">The address range of the stack is useful for piecing together interleaved stack traces gathered from multiple debugging engines.</span></span> <span data-ttu-id="26b59-110">數字範圍提供內容的堆疊框架的任何資訊。</span><span class="sxs-lookup"><span data-stu-id="26b59-110">The numeric range provides no information about the contents of the stack frame.</span></span> <span data-ttu-id="26b59-111">它是僅對比較的堆疊框架位置有意義。</span><span class="sxs-lookup"><span data-stu-id="26b59-111">It is meaningful only for comparison of stack frame locations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26b59-112">需求</span><span class="sxs-lookup"><span data-stu-id="26b59-112">Requirements</span></span>  
 <span data-ttu-id="26b59-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="26b59-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26b59-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="26b59-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26b59-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26b59-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26b59-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26b59-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
