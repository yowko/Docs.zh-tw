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
ms.openlocfilehash: a5b9d57aab834ba3ca72a2ea8576ec70cd88eb77
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713570"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a><span data-ttu-id="e0d83-102">ICorDebugProcess2::GetReferenceValueFromGCHandle 方法</span><span class="sxs-lookup"><span data-stu-id="e0d83-102">ICorDebugProcess2::GetReferenceValueFromGCHandle Method</span></span>

<span data-ttu-id="e0d83-103">取得具有垃圾收集控制碼之指定 managed 物件的參考指標。</span><span class="sxs-lookup"><span data-stu-id="e0d83-103">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0d83-104">語法</span><span class="sxs-lookup"><span data-stu-id="e0d83-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0d83-105">參數</span><span class="sxs-lookup"><span data-stu-id="e0d83-105">Parameters</span></span>  

 `handle`  
 <span data-ttu-id="e0d83-106">在具有垃圾收集控制碼之 managed 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="e0d83-106">[in] A pointer to a managed object that has a garbage collection handle.</span></span> <span data-ttu-id="e0d83-107">這個值是一個 <xref:System.IntPtr> 物件，可以從 <xref:System.Runtime.InteropServices.GCHandle> managed 物件的取得。</span><span class="sxs-lookup"><span data-stu-id="e0d83-107">This value is a <xref:System.IntPtr> object and can be retrieved from the <xref:System.Runtime.InteropServices.GCHandle> for the managed object.</span></span>  
  
 `pOutValue`  
 <span data-ttu-id="e0d83-108">擴展ICorDebugReferenceValue 物件位址的指標，該物件表示指定之 managed 物件的參考。</span><span class="sxs-lookup"><span data-stu-id="e0d83-108">[out] A pointer to the address of an ICorDebugReferenceValue object that represents a reference to the specified managed object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0d83-109">備註</span><span class="sxs-lookup"><span data-stu-id="e0d83-109">Remarks</span></span>  

 <span data-ttu-id="e0d83-110">請勿將傳回的參考值與垃圾收集參考值混淆。</span><span class="sxs-lookup"><span data-stu-id="e0d83-110">Do not confuse the returned reference value with a garbage collection reference value.</span></span>  
  
 <span data-ttu-id="e0d83-111">傳回的參考行為類似一般參考。</span><span class="sxs-lookup"><span data-stu-id="e0d83-111">The returned reference behaves like a normal reference.</span></span> <span data-ttu-id="e0d83-112">當程式碼執行在中斷點之後繼續時，就會停用此功能。</span><span class="sxs-lookup"><span data-stu-id="e0d83-112">It is disabled when code execution continues after a breakpoint.</span></span> <span data-ttu-id="e0d83-113">目標物件的存留期不會受到參考值的存留期所影響。</span><span class="sxs-lookup"><span data-stu-id="e0d83-113">The lifetime of the target object is not affected by the lifetime of the reference value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e0d83-114">`GetReferenceValueFromGCHandle`方法不會驗證控制碼。</span><span class="sxs-lookup"><span data-stu-id="e0d83-114">The `GetReferenceValueFromGCHandle` method does not validate the handle.</span></span> <span data-ttu-id="e0d83-115">因此， `GetReferenceValueFromGCHandle` 當傳遞的控制碼無效時，方法可能會損毀偵錯工具和正在進行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e0d83-115">Therefore, the `GetReferenceValueFromGCHandle` method can potentially corrupt both the debugger and the code being debugged if an invalid handle is passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0d83-116">需求</span><span class="sxs-lookup"><span data-stu-id="e0d83-116">Requirements</span></span>  

 <span data-ttu-id="e0d83-117">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e0d83-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0d83-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e0d83-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0d83-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0d83-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0d83-120">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0d83-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
