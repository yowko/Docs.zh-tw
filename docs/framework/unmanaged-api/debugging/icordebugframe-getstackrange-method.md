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
ms.openlocfilehash: 7a35ce025360e0ec8b7085d68e54548026b7c7fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178903"
---
# <a name="icordebugframegetstackrange-method"></a><span data-ttu-id="b4743-102">ICorDebugFrame::GetStackRange 方法</span><span class="sxs-lookup"><span data-stu-id="b4743-102">ICorDebugFrame::GetStackRange Method</span></span>
<span data-ttu-id="b4743-103">獲取此堆疊幀的絕對位址範圍。</span><span class="sxs-lookup"><span data-stu-id="b4743-103">Gets the absolute address range of this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4743-104">語法</span><span class="sxs-lookup"><span data-stu-id="b4743-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4743-105">參數</span><span class="sxs-lookup"><span data-stu-id="b4743-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="b4743-106">[出]指向`CORDB_ADDRESS`指定此`ICorDebugFrame`物件表示的堆疊幀的起始位址的指標。</span><span class="sxs-lookup"><span data-stu-id="b4743-106">[out] A pointer to a `CORDB_ADDRESS` that specifies the starting address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="b4743-107">[出]指向`CORDB_ADDRESS`指定此`ICorDebugFrame`物件表示的堆疊幀的結束位址的指標。</span><span class="sxs-lookup"><span data-stu-id="b4743-107">[out] A pointer to a `CORDB_ADDRESS` that specifies the ending address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4743-108">備註</span><span class="sxs-lookup"><span data-stu-id="b4743-108">Remarks</span></span>  
 <span data-ttu-id="b4743-109">堆疊的位址範圍可用於拼湊從多個調試引擎收集的交錯堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="b4743-109">The address range of the stack is useful for piecing together interleaved stack traces gathered from multiple debugging engines.</span></span> <span data-ttu-id="b4743-110">數值範圍不提供有關堆疊幀內容的資訊。</span><span class="sxs-lookup"><span data-stu-id="b4743-110">The numeric range provides no information about the contents of the stack frame.</span></span> <span data-ttu-id="b4743-111">它僅對堆疊幀位置的比較有意義。</span><span class="sxs-lookup"><span data-stu-id="b4743-111">It is meaningful only for comparison of stack frame locations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4743-112">需求</span><span class="sxs-lookup"><span data-stu-id="b4743-112">Requirements</span></span>  
 <span data-ttu-id="b4743-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b4743-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4743-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4743-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4743-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4743-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4743-116">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4743-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
