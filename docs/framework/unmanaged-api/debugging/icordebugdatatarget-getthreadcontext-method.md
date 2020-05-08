---
title: ICorDebugDataTarget::GetThreadContext 方法
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetThreadContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetThreadContext
helpviewer_keywords:
- ICorDebugDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: c8954268-1821-4b23-b665-dbb55f2af31b
topic_type:
- apiref
ms.openlocfilehash: 79708aa5a2abcb8d7465f82a8beb918484c193b9
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976547"
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a><span data-ttu-id="c42cf-102">ICorDebugDataTarget::GetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="c42cf-102">ICorDebugDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="c42cf-103">傳回指定之執行緒的目前線程內容。</span><span class="sxs-lookup"><span data-stu-id="c42cf-103">Returns the current thread context for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c42cf-104">語法</span><span class="sxs-lookup"><span data-stu-id="c42cf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c42cf-105">參數</span><span class="sxs-lookup"><span data-stu-id="c42cf-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="c42cf-106">在要抓取其內容之執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="c42cf-106">[in] The identifier of the thread whose context is to be retrieved.</span></span> <span data-ttu-id="c42cf-107">識別碼是由作業系統所定義。</span><span class="sxs-lookup"><span data-stu-id="c42cf-107">The identifier is defined by the operating system.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="c42cf-108">在平臺相依旗標的位元組合，表示應該讀取內容的哪個部分。</span><span class="sxs-lookup"><span data-stu-id="c42cf-108">[in] A bitwise combination of platform-dependent flags that indicate which portions of the context should be read.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="c42cf-109">[in] `pContext` 的大小。</span><span class="sxs-lookup"><span data-stu-id="c42cf-109">[in] The size of `pContext`.</span></span>  
  
 `pContext`  
 <span data-ttu-id="c42cf-110">脫銷將儲存執行緒內容的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="c42cf-110">[out] The buffer where the thread context will be stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c42cf-111">備註</span><span class="sxs-lookup"><span data-stu-id="c42cf-111">Remarks</span></span>  
 <span data-ttu-id="c42cf-112">在 Windows 平臺上`pContext` ，必須是`CONTEXT`適用于[ICorDebugDataTarget：： GetPlatform](icordebugdatatarget-getplatform-method.md)方法所指定之電腦類型的結構（定義于 WinNT. h）。</span><span class="sxs-lookup"><span data-stu-id="c42cf-112">On Windows platforms, `pContext` must be a `CONTEXT` structure (defined in WinNT.h) that is appropriate for the machine type specified by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="c42cf-113">`contextFlags`必須具有與`ContextFlags` `CONTEXT`結構的欄位相同的值。</span><span class="sxs-lookup"><span data-stu-id="c42cf-113">`contextFlags` must have the same values as the `ContextFlags` field of the `CONTEXT` structure.</span></span> <span data-ttu-id="c42cf-114">結構`CONTEXT`是處理器特定的;如需詳細資訊，請參閱 WinNT. h 檔案。</span><span class="sxs-lookup"><span data-stu-id="c42cf-114">The `CONTEXT` structure is processor-specific; refer to the WinNT.h file for details.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c42cf-115">需求</span><span class="sxs-lookup"><span data-stu-id="c42cf-115">Requirements</span></span>  
 <span data-ttu-id="c42cf-116">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c42cf-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c42cf-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c42cf-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c42cf-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c42cf-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c42cf-119">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c42cf-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c42cf-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c42cf-120">See also</span></span>

- [<span data-ttu-id="c42cf-121">ICorDebugDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="c42cf-121">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="c42cf-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="c42cf-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c42cf-123">偵錯</span><span class="sxs-lookup"><span data-stu-id="c42cf-123">Debugging</span></span>](index.md)
