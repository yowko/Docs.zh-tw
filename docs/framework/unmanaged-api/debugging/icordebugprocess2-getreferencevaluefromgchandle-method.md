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
ms.openlocfilehash: 47647bf0460507b4c88b47bf87bfcc3bf620aecc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137214"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a><span data-ttu-id="0bf77-102">ICorDebugProcess2::GetReferenceValueFromGCHandle 方法</span><span class="sxs-lookup"><span data-stu-id="0bf77-102">ICorDebugProcess2::GetReferenceValueFromGCHandle Method</span></span>
<span data-ttu-id="0bf77-103">取得具有垃圾收集控制碼之指定 managed 物件的參考指標。</span><span class="sxs-lookup"><span data-stu-id="0bf77-103">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bf77-104">語法</span><span class="sxs-lookup"><span data-stu-id="0bf77-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0bf77-105">參數</span><span class="sxs-lookup"><span data-stu-id="0bf77-105">Parameters</span></span>  
 `handle`  
 <span data-ttu-id="0bf77-106">在具有垃圾收集控制碼之 managed 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="0bf77-106">[in] A pointer to a managed object that has a garbage collection handle.</span></span> <span data-ttu-id="0bf77-107">這個值是 <xref:System.IntPtr> 物件，而且可以從受管理物件的 <xref:System.Runtime.InteropServices.GCHandle> 中抓取。</span><span class="sxs-lookup"><span data-stu-id="0bf77-107">This value is a <xref:System.IntPtr> object and can be retrieved from the <xref:System.Runtime.InteropServices.GCHandle> for the managed object.</span></span>  
  
 `pOutValue`  
 <span data-ttu-id="0bf77-108">脫銷ICorDebugReferenceValue 物件位址的指標，表示指定之 managed 物件的參考。</span><span class="sxs-lookup"><span data-stu-id="0bf77-108">[out] A pointer to the address of an ICorDebugReferenceValue object that represents a reference to the specified managed object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bf77-109">備註</span><span class="sxs-lookup"><span data-stu-id="0bf77-109">Remarks</span></span>  
 <span data-ttu-id="0bf77-110">請勿混淆傳回的參考值與垃圾收集參考值。</span><span class="sxs-lookup"><span data-stu-id="0bf77-110">Do not confuse the returned reference value with a garbage collection reference value.</span></span>  
  
 <span data-ttu-id="0bf77-111">傳回的參考與一般參考的行為類似。</span><span class="sxs-lookup"><span data-stu-id="0bf77-111">The returned reference behaves like a normal reference.</span></span> <span data-ttu-id="0bf77-112">當程式碼在中斷點之後繼續執行時，就會停用它。</span><span class="sxs-lookup"><span data-stu-id="0bf77-112">It is disabled when code execution continues after a breakpoint.</span></span> <span data-ttu-id="0bf77-113">目標物件的存留期不會受到參考值的存留期影響。</span><span class="sxs-lookup"><span data-stu-id="0bf77-113">The lifetime of the target object is not affected by the lifetime of the reference value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0bf77-114">`GetReferenceValueFromGCHandle` 方法不會驗證控制碼。</span><span class="sxs-lookup"><span data-stu-id="0bf77-114">The `GetReferenceValueFromGCHandle` method does not validate the handle.</span></span> <span data-ttu-id="0bf77-115">因此，如果傳遞了不正確控制碼，`GetReferenceValueFromGCHandle` 方法可能會損毀偵錯工具和正在進行調試的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0bf77-115">Therefore, the `GetReferenceValueFromGCHandle` method can potentially corrupt both the debugger and the code being debugged if an invalid handle is passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bf77-116">需求</span><span class="sxs-lookup"><span data-stu-id="0bf77-116">Requirements</span></span>  
 <span data-ttu-id="0bf77-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0bf77-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bf77-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0bf77-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0bf77-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0bf77-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0bf77-120">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bf77-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
