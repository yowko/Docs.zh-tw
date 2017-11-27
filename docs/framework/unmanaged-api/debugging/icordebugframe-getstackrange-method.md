---
title: "ICorDebugFrame::GetStackRange 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame.GetStackRange
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame::GetStackRange
helpviewer_keywords:
- GetStackRange method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetStackRange method [.NET Framework debugging]
ms.assetid: fab037cb-fda6-40fb-9367-921e435dd5a0
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f1db7617d52e07489ade339b76023e21816835ee
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugframegetstackrange-method"></a><span data-ttu-id="8d4c8-102">ICorDebugFrame::GetStackRange 方法</span><span class="sxs-lookup"><span data-stu-id="8d4c8-102">ICorDebugFrame::GetStackRange Method</span></span>
<span data-ttu-id="8d4c8-103">取得此堆疊框架的絕對位址範圍。</span><span class="sxs-lookup"><span data-stu-id="8d4c8-103">Gets the absolute address range of this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d4c8-104">語法</span><span class="sxs-lookup"><span data-stu-id="8d4c8-104">Syntax</span></span>  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8d4c8-105">參數</span><span class="sxs-lookup"><span data-stu-id="8d4c8-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="8d4c8-106">[out]指標`CORDB_ADDRESS`，指定所表示的堆疊框架的起始位址`ICorDebugFrame`物件。</span><span class="sxs-lookup"><span data-stu-id="8d4c8-106">[out] A pointer to a `CORDB_ADDRESS` that specifies the starting address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="8d4c8-107">[out]指標`CORDB_ADDRESS`，指定所表示之堆疊框架的結束位址`ICorDebugFrame`物件。</span><span class="sxs-lookup"><span data-stu-id="8d4c8-107">[out] A pointer to a `CORDB_ADDRESS` that specifies the ending address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d4c8-108">備註</span><span class="sxs-lookup"><span data-stu-id="8d4c8-108">Remarks</span></span>  
 <span data-ttu-id="8d4c8-109">堆疊的位址範圍可用於拼湊交錯的堆疊追蹤所蒐集從多個偵錯引擎。</span><span class="sxs-lookup"><span data-stu-id="8d4c8-109">The address range of the stack is useful for piecing together interleaved stack traces gathered from multiple debugging engines.</span></span> <span data-ttu-id="8d4c8-110">數字範圍提供內容的堆疊框架的任何資訊。</span><span class="sxs-lookup"><span data-stu-id="8d4c8-110">The numeric range provides no information about the contents of the stack frame.</span></span> <span data-ttu-id="8d4c8-111">它是才有意義的堆疊框架位置的比較。</span><span class="sxs-lookup"><span data-stu-id="8d4c8-111">It is meaningful only for comparison of stack frame locations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d4c8-112">需求</span><span class="sxs-lookup"><span data-stu-id="8d4c8-112">Requirements</span></span>  
 <span data-ttu-id="8d4c8-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8d4c8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d4c8-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8d4c8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d4c8-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d4c8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d4c8-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d4c8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
