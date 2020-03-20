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
ms.openlocfilehash: c7a1bf3cb10cbc8cdae2788b45e1badaf66a9dbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178885"
---
# <a name="icordebugheapvalue2createhandle-method"></a><span data-ttu-id="7d1d1-102">ICorDebugHeapValue2::CreateHandle 方法</span><span class="sxs-lookup"><span data-stu-id="7d1d1-102">ICorDebugHeapValue2::CreateHandle Method</span></span>
<span data-ttu-id="7d1d1-103">為此 ICorDebugHeapValue2 物件表示的堆值創建指定類型的控制碼。</span><span class="sxs-lookup"><span data-stu-id="7d1d1-103">Creates a handle of the specified type for the heap value represented by this ICorDebugHeapValue2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d1d1-104">語法</span><span class="sxs-lookup"><span data-stu-id="7d1d1-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d1d1-105">參數</span><span class="sxs-lookup"><span data-stu-id="7d1d1-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="7d1d1-106">[在]CorDebugHandleType 枚舉的值，用於指定要創建的控制碼的類型。</span><span class="sxs-lookup"><span data-stu-id="7d1d1-106">[in] A value of the CorDebugHandleType enumeration that specifies the type of handle to be created.</span></span>  
  
 `ppHandle`  
 <span data-ttu-id="7d1d1-107">[出]指向 ICorDebugHandleValue 物件的位址的指標，該物件表示此堆值的新控制碼。</span><span class="sxs-lookup"><span data-stu-id="7d1d1-107">[out] A pointer to the address of an ICorDebugHandleValue object that represents the new handle for this heap value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d1d1-108">備註</span><span class="sxs-lookup"><span data-stu-id="7d1d1-108">Remarks</span></span>  
 <span data-ttu-id="7d1d1-109">該控制碼將在與堆值關聯的應用程式域中創建，如果卸載應用程式域，該控制碼將變為無效。</span><span class="sxs-lookup"><span data-stu-id="7d1d1-109">The handle will be created in the application domain that is associated with the heap value, and will become invalid if the application domain gets unloaded.</span></span>  
  
 <span data-ttu-id="7d1d1-110">對同一堆值的多次調用將創建多個控制碼。</span><span class="sxs-lookup"><span data-stu-id="7d1d1-110">Multiple calls to this function for the same heap value will create multiple handles.</span></span> <span data-ttu-id="7d1d1-111">由於控制碼會影響垃圾回收器的性能，調試器應將其限制為一次處於活動狀態的相對較少的控制碼（約 256）。</span><span class="sxs-lookup"><span data-stu-id="7d1d1-111">Because handles affect the performance of the garbage collector, the debugger should limit itself to a relatively small number of handles (about 256) that are active at a time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d1d1-112">需求</span><span class="sxs-lookup"><span data-stu-id="7d1d1-112">Requirements</span></span>  
 <span data-ttu-id="7d1d1-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7d1d1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d1d1-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7d1d1-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d1d1-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d1d1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d1d1-116">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d1d1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
