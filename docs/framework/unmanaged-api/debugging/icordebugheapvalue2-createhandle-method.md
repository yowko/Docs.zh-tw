---
title: "ICorDebugHeapValue2::CreateHandle 方法"
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
- ICorDebugHeapValue2.CreateHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue2::CreateHandle
helpviewer_keywords:
- CreateHandle method [.NET Framework debugging]
- ICorDebugHeapValue2::CreateHandle method [.NET Framework debugging]
ms.assetid: fbc418e8-fa22-420d-84ec-e0e1800db041
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: eeef3215c3740cdaa7d1b78b73fde9e76d7b40c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapvalue2createhandle-method"></a><span data-ttu-id="68d65-102">ICorDebugHeapValue2::CreateHandle 方法</span><span class="sxs-lookup"><span data-stu-id="68d65-102">ICorDebugHeapValue2::CreateHandle Method</span></span>
<span data-ttu-id="68d65-103">建立這個 ICorDebugHeapValue2 物件所代表的堆積值的指定類型的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="68d65-103">Creates a handle of the specified type for the heap value represented by this ICorDebugHeapValue2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68d65-104">語法</span><span class="sxs-lookup"><span data-stu-id="68d65-104">Syntax</span></span>  
  
```  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,   
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="68d65-105">參數</span><span class="sxs-lookup"><span data-stu-id="68d65-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="68d65-106">[in]CorDebugHandleType 列舉，指定建立控制代碼類型的值。</span><span class="sxs-lookup"><span data-stu-id="68d65-106">[in] A value of the CorDebugHandleType enumeration that specifies the type of handle to be created.</span></span>  
  
 `ppHandle`  
 <span data-ttu-id="68d65-107">[out]ICorDebugHandleValue 物件，表示新控制代碼，此堆積值的位址指標。</span><span class="sxs-lookup"><span data-stu-id="68d65-107">[out] A pointer to the address of an ICorDebugHandleValue object that represents the new handle for this heap value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68d65-108">備註</span><span class="sxs-lookup"><span data-stu-id="68d65-108">Remarks</span></span>  
 <span data-ttu-id="68d65-109">控制代碼會在堆積的值，與相關聯的應用程式定義域中建立，且會變成無效，如果應用程式定義域卸載。</span><span class="sxs-lookup"><span data-stu-id="68d65-109">The handle will be created in the application domain that is associated with the heap value, and will become invalid if the application domain gets unloaded.</span></span>  
  
 <span data-ttu-id="68d65-110">多次呼叫此函式相同的堆積值將會建立多個控制代碼。</span><span class="sxs-lookup"><span data-stu-id="68d65-110">Multiple calls to this function for the same heap value will create multiple handles.</span></span> <span data-ttu-id="68d65-111">控制代碼會影響記憶體回收行程的效能，因為偵錯工具應該限制為本身相對較小的數字的時間在使用中的控制代碼 (大約 256)。</span><span class="sxs-lookup"><span data-stu-id="68d65-111">Because handles affect the performance of the garbage collector, the debugger should limit itself to a relatively small number of handles (about 256) that are active at a time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68d65-112">需求</span><span class="sxs-lookup"><span data-stu-id="68d65-112">Requirements</span></span>  
 <span data-ttu-id="68d65-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="68d65-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68d65-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68d65-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68d65-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68d65-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68d65-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68d65-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
