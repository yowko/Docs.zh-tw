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
ms.openlocfilehash: cacdccf5c27cd1d115134d49e754b4ace2870b72
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205152"
---
# <a name="icordebugframegetstackrange-method"></a><span data-ttu-id="37978-102">ICorDebugFrame::GetStackRange 方法</span><span class="sxs-lookup"><span data-stu-id="37978-102">ICorDebugFrame::GetStackRange Method</span></span>
<span data-ttu-id="37978-103">取得這個堆疊框架的絕對位址範圍。</span><span class="sxs-lookup"><span data-stu-id="37978-103">Gets the absolute address range of this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37978-104">語法</span><span class="sxs-lookup"><span data-stu-id="37978-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37978-105">參數</span><span class="sxs-lookup"><span data-stu-id="37978-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="37978-106">脫銷的指標 `CORDB_ADDRESS` ，指定此物件所表示之堆疊框架的起始位址 `ICorDebugFrame` 。</span><span class="sxs-lookup"><span data-stu-id="37978-106">[out] A pointer to a `CORDB_ADDRESS` that specifies the starting address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="37978-107">脫銷的指標 `CORDB_ADDRESS` ，指定此物件所表示之堆疊框架的結束位址 `ICorDebugFrame` 。</span><span class="sxs-lookup"><span data-stu-id="37978-107">[out] A pointer to a `CORDB_ADDRESS` that specifies the ending address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37978-108">備註</span><span class="sxs-lookup"><span data-stu-id="37978-108">Remarks</span></span>  
 <span data-ttu-id="37978-109">堆疊的位址範圍適用于將從多個偵錯工具收集而來的交錯堆疊追蹤 piecing 在一起。</span><span class="sxs-lookup"><span data-stu-id="37978-109">The address range of the stack is useful for piecing together interleaved stack traces gathered from multiple debugging engines.</span></span> <span data-ttu-id="37978-110">此數值範圍不會提供有關堆疊框架之內容的資訊。</span><span class="sxs-lookup"><span data-stu-id="37978-110">The numeric range provides no information about the contents of the stack frame.</span></span> <span data-ttu-id="37978-111">只有在比較堆疊框架位置時才有意義。</span><span class="sxs-lookup"><span data-stu-id="37978-111">It is meaningful only for comparison of stack frame locations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37978-112">需求</span><span class="sxs-lookup"><span data-stu-id="37978-112">Requirements</span></span>  
 <span data-ttu-id="37978-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="37978-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37978-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="37978-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37978-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37978-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37978-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37978-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
