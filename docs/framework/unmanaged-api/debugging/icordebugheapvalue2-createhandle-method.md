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
ms.openlocfilehash: 278120c6e1bc87a061a3f81f71bdb7b89cd421be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726557"
---
# <a name="icordebugheapvalue2createhandle-method"></a><span data-ttu-id="67dfd-102">ICorDebugHeapValue2::CreateHandle 方法</span><span class="sxs-lookup"><span data-stu-id="67dfd-102">ICorDebugHeapValue2::CreateHandle Method</span></span>

<span data-ttu-id="67dfd-103">針對這個 ICorDebugHeapValue2 物件所表示的堆積值，建立指定之類型的控制碼。</span><span class="sxs-lookup"><span data-stu-id="67dfd-103">Creates a handle of the specified type for the heap value represented by this ICorDebugHeapValue2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67dfd-104">語法</span><span class="sxs-lookup"><span data-stu-id="67dfd-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67dfd-105">參數</span><span class="sxs-lookup"><span data-stu-id="67dfd-105">Parameters</span></span>  

 `type`  
 <span data-ttu-id="67dfd-106">在CorDebugHandleType 列舉的值，這個值會指定要建立之控制碼的類型。</span><span class="sxs-lookup"><span data-stu-id="67dfd-106">[in] A value of the CorDebugHandleType enumeration that specifies the type of handle to be created.</span></span>  
  
 `ppHandle`  
 <span data-ttu-id="67dfd-107">擴展ICorDebugHandleValue 物件位址的指標，該物件表示這個堆積值的新控制碼。</span><span class="sxs-lookup"><span data-stu-id="67dfd-107">[out] A pointer to the address of an ICorDebugHandleValue object that represents the new handle for this heap value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67dfd-108">備註</span><span class="sxs-lookup"><span data-stu-id="67dfd-108">Remarks</span></span>  

 <span data-ttu-id="67dfd-109">系統會在與堆積值相關聯的應用程式域中建立控制碼，如果已卸載應用程式域，則會變成無效。</span><span class="sxs-lookup"><span data-stu-id="67dfd-109">The handle will be created in the application domain that is associated with the heap value, and will become invalid if the application domain gets unloaded.</span></span>  
  
 <span data-ttu-id="67dfd-110">對相同堆積值的這個函式有多個呼叫會建立多個控制碼。</span><span class="sxs-lookup"><span data-stu-id="67dfd-110">Multiple calls to this function for the same heap value will create multiple handles.</span></span> <span data-ttu-id="67dfd-111">由於處理常式會影響垃圾收集行程的效能，因此偵錯工具應該將其本身限制為相對較少的控制碼數目， (大約每次使用中的 256) 。</span><span class="sxs-lookup"><span data-stu-id="67dfd-111">Because handles affect the performance of the garbage collector, the debugger should limit itself to a relatively small number of handles (about 256) that are active at a time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67dfd-112">需求</span><span class="sxs-lookup"><span data-stu-id="67dfd-112">Requirements</span></span>  

 <span data-ttu-id="67dfd-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="67dfd-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67dfd-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67dfd-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67dfd-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67dfd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67dfd-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67dfd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
