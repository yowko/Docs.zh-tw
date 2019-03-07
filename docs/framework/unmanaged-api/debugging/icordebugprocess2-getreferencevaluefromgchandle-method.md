---
title: ICorDebugProcess2::GetReferenceValueFromGCHandle 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetReferenceValueFromGCHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetReferenceValueFromGCHandle
helpviewer_keywords:
- GetReferenceValueFromGCHandle method [.NET Framework debugging]
- ICorDebugProcess2::GetReferenceValueFromGCHandle method [.NET Framework debugging]
ms.assetid: 8bdd7f4c-19f2-4ede-875e-603773e8c128
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08bf4022f7cd7f85ffe7939c16fd47950e131a77
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471520"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a><span data-ttu-id="696e0-102">ICorDebugProcess2::GetReferenceValueFromGCHandle 方法</span><span class="sxs-lookup"><span data-stu-id="696e0-102">ICorDebugProcess2::GetReferenceValueFromGCHandle Method</span></span>
<span data-ttu-id="696e0-103">取得指定已處理的記憶體回收的 managed 物件的參考指標。</span><span class="sxs-lookup"><span data-stu-id="696e0-103">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="696e0-104">語法</span><span class="sxs-lookup"><span data-stu-id="696e0-104">Syntax</span></span>  
  
```  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="696e0-105">參數</span><span class="sxs-lookup"><span data-stu-id="696e0-105">Parameters</span></span>  
 `handle`  
 <span data-ttu-id="696e0-106">[in]具有記憶體回收控制代碼的 managed 物件指標。</span><span class="sxs-lookup"><span data-stu-id="696e0-106">[in] A pointer to a managed object that has a garbage collection handle.</span></span> <span data-ttu-id="696e0-107">這個值是<xref:System.IntPtr>物件，並可從擷取<xref:System.Runtime.InteropServices.GCHandle>針對受管理的物件。</span><span class="sxs-lookup"><span data-stu-id="696e0-107">This value is a <xref:System.IntPtr> object and can be retrieved from the <xref:System.Runtime.InteropServices.GCHandle> for the managed object.</span></span>  
  
 `pOutValue`  
 <span data-ttu-id="696e0-108">[out]ICorDebugReferenceValue 物件，表示指定的受管理物件的參考的位址指標。</span><span class="sxs-lookup"><span data-stu-id="696e0-108">[out] A pointer to the address of an ICorDebugReferenceValue object that represents a reference to the specified managed object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="696e0-109">備註</span><span class="sxs-lookup"><span data-stu-id="696e0-109">Remarks</span></span>  
 <span data-ttu-id="696e0-110">請勿混淆廢棄項目集合的參考值傳回的參考值。</span><span class="sxs-lookup"><span data-stu-id="696e0-110">Do not confuse the returned reference value with a garbage collection reference value.</span></span>  
  
 <span data-ttu-id="696e0-111">傳回的參考作用如同一般的參考。</span><span class="sxs-lookup"><span data-stu-id="696e0-111">The returned reference behaves like a normal reference.</span></span> <span data-ttu-id="696e0-112">當在中斷點後繼續執行程式碼時，它會停用。</span><span class="sxs-lookup"><span data-stu-id="696e0-112">It is disabled when code execution continues after a breakpoint.</span></span> <span data-ttu-id="696e0-113">目標物件的存留期間不會受到參考值的存留期。</span><span class="sxs-lookup"><span data-stu-id="696e0-113">The lifetime of the target object is not affected by the lifetime of the reference value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="696e0-114">`GetReferenceValueFromGCHandle`方法不會驗證此控制代碼。</span><span class="sxs-lookup"><span data-stu-id="696e0-114">The `GetReferenceValueFromGCHandle` method does not validate the handle.</span></span> <span data-ttu-id="696e0-115">因此，`GetReferenceValueFromGCHandle`偵錯工具和正在偵錯，如果傳遞無效的控制代碼的程式碼，方法可能會毀損。</span><span class="sxs-lookup"><span data-stu-id="696e0-115">Therefore, the `GetReferenceValueFromGCHandle` method can potentially corrupt both the debugger and the code being debugged if an invalid handle is passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="696e0-116">需求</span><span class="sxs-lookup"><span data-stu-id="696e0-116">Requirements</span></span>  
 <span data-ttu-id="696e0-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="696e0-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="696e0-118">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="696e0-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="696e0-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="696e0-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="696e0-120">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="696e0-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
