---
title: ICorDebugHeapValue2::CreateHandle 方法
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da5c5a12df5689f113857045ba4bcda696bda8f5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756721"
---
# <a name="icordebugheapvalue2createhandle-method"></a><span data-ttu-id="01109-102">ICorDebugHeapValue2::CreateHandle 方法</span><span class="sxs-lookup"><span data-stu-id="01109-102">ICorDebugHeapValue2::CreateHandle Method</span></span>
<span data-ttu-id="01109-103">建立堆積值，這個 ICorDebugHeapValue2 物件所表示的指定類型的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="01109-103">Creates a handle of the specified type for the heap value represented by this ICorDebugHeapValue2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01109-104">語法</span><span class="sxs-lookup"><span data-stu-id="01109-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,   
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01109-105">參數</span><span class="sxs-lookup"><span data-stu-id="01109-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="01109-106">[in]CorDebugHandleType 列舉，指定要建立的控制代碼的型別值。</span><span class="sxs-lookup"><span data-stu-id="01109-106">[in] A value of the CorDebugHandleType enumeration that specifies the type of handle to be created.</span></span>  
  
 `ppHandle`  
 <span data-ttu-id="01109-107">[out]ICorDebugHandleValue 物件，表示此堆積值的新控制代碼的位址指標。</span><span class="sxs-lookup"><span data-stu-id="01109-107">[out] A pointer to the address of an ICorDebugHandleValue object that represents the new handle for this heap value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01109-108">備註</span><span class="sxs-lookup"><span data-stu-id="01109-108">Remarks</span></span>  
 <span data-ttu-id="01109-109">控制代碼會在堆積的值，與相關聯的應用程式定義域中建立，而且會變成無效，如果應用程式定義域卸載。</span><span class="sxs-lookup"><span data-stu-id="01109-109">The handle will be created in the application domain that is associated with the heap value, and will become invalid if the application domain gets unloaded.</span></span>  
  
 <span data-ttu-id="01109-110">此函式相同的堆積值的多個呼叫會建立多個控制代碼。</span><span class="sxs-lookup"><span data-stu-id="01109-110">Multiple calls to this function for the same heap value will create multiple handles.</span></span> <span data-ttu-id="01109-111">控制代碼會影響記憶體回收行程的效能，因為偵錯工具應限制本身相對較小的數字，一次是作用中的控制代碼 (大約 256)。</span><span class="sxs-lookup"><span data-stu-id="01109-111">Because handles affect the performance of the garbage collector, the debugger should limit itself to a relatively small number of handles (about 256) that are active at a time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01109-112">需求</span><span class="sxs-lookup"><span data-stu-id="01109-112">Requirements</span></span>  
 <span data-ttu-id="01109-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="01109-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01109-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01109-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01109-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01109-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01109-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01109-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
