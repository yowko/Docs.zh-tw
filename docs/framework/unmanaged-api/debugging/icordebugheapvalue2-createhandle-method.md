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
ms.openlocfilehash: cbc056e9a3cc00178b32dee4011da4403dff508a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212772"
---
# <a name="icordebugheapvalue2createhandle-method"></a><span data-ttu-id="bfb52-102">ICorDebugHeapValue2::CreateHandle 方法</span><span class="sxs-lookup"><span data-stu-id="bfb52-102">ICorDebugHeapValue2::CreateHandle Method</span></span>
<span data-ttu-id="bfb52-103">針對這個 ICorDebugHeapValue2 物件所表示的堆積值，建立指定類型的控制碼。</span><span class="sxs-lookup"><span data-stu-id="bfb52-103">Creates a handle of the specified type for the heap value represented by this ICorDebugHeapValue2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfb52-104">語法</span><span class="sxs-lookup"><span data-stu-id="bfb52-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bfb52-105">參數</span><span class="sxs-lookup"><span data-stu-id="bfb52-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="bfb52-106">在CorDebugHandleType 列舉的值，指定要建立的控制碼類型。</span><span class="sxs-lookup"><span data-stu-id="bfb52-106">[in] A value of the CorDebugHandleType enumeration that specifies the type of handle to be created.</span></span>  
  
 `ppHandle`  
 <span data-ttu-id="bfb52-107">脫銷ICorDebugHandleValue 物件位址的指標，表示這個堆積值的新控制碼。</span><span class="sxs-lookup"><span data-stu-id="bfb52-107">[out] A pointer to the address of an ICorDebugHandleValue object that represents the new handle for this heap value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bfb52-108">備註</span><span class="sxs-lookup"><span data-stu-id="bfb52-108">Remarks</span></span>  
 <span data-ttu-id="bfb52-109">系統會在與堆積值相關聯的應用程式域中建立控制碼，如果已卸載應用程式域，將會變成無效。</span><span class="sxs-lookup"><span data-stu-id="bfb52-109">The handle will be created in the application domain that is associated with the heap value, and will become invalid if the application domain gets unloaded.</span></span>  
  
 <span data-ttu-id="bfb52-110">針對相同堆積值多次呼叫此函式，將會建立多個控制碼。</span><span class="sxs-lookup"><span data-stu-id="bfb52-110">Multiple calls to this function for the same heap value will create multiple handles.</span></span> <span data-ttu-id="bfb52-111">由於控制碼會影響垃圾收集行程的效能，因此偵錯工具應該將其本身限制為一次作用中的相對較少控制碼（大約256）。</span><span class="sxs-lookup"><span data-stu-id="bfb52-111">Because handles affect the performance of the garbage collector, the debugger should limit itself to a relatively small number of handles (about 256) that are active at a time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfb52-112">需求</span><span class="sxs-lookup"><span data-stu-id="bfb52-112">Requirements</span></span>  
 <span data-ttu-id="bfb52-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bfb52-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfb52-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bfb52-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bfb52-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bfb52-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bfb52-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfb52-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
