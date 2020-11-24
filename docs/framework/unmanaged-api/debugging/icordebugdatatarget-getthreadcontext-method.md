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
ms.openlocfilehash: faacea6a2f04ef20025fd33adb4ce76eaf54f32c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679737"
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a><span data-ttu-id="f1f00-102">ICorDebugDataTarget::GetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="f1f00-102">ICorDebugDataTarget::GetThreadContext Method</span></span>

<span data-ttu-id="f1f00-103">傳回指定執行緒目前的執行緒內容。</span><span class="sxs-lookup"><span data-stu-id="f1f00-103">Returns the current thread context for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1f00-104">語法</span><span class="sxs-lookup"><span data-stu-id="f1f00-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1f00-105">參數</span><span class="sxs-lookup"><span data-stu-id="f1f00-105">Parameters</span></span>  

 `dwThreadID`  
 <span data-ttu-id="f1f00-106">在要取出其內容之執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="f1f00-106">[in] The identifier of the thread whose context is to be retrieved.</span></span> <span data-ttu-id="f1f00-107">此識別碼是由作業系統定義。</span><span class="sxs-lookup"><span data-stu-id="f1f00-107">The identifier is defined by the operating system.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="f1f00-108">在平臺相依旗標的位元組合，表示應讀取內容的哪些部分。</span><span class="sxs-lookup"><span data-stu-id="f1f00-108">[in] A bitwise combination of platform-dependent flags that indicate which portions of the context should be read.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="f1f00-109">[in] `pContext` 的大小。</span><span class="sxs-lookup"><span data-stu-id="f1f00-109">[in] The size of `pContext`.</span></span>  
  
 `pContext`  
 <span data-ttu-id="f1f00-110">擴展將儲存執行緒內容的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f1f00-110">[out] The buffer where the thread context will be stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1f00-111">備註</span><span class="sxs-lookup"><span data-stu-id="f1f00-111">Remarks</span></span>  

 <span data-ttu-id="f1f00-112">在 Windows 平臺上， `pContext` 必須是 `CONTEXT` 在 WinNT. h) 中定義的結構 (，適用于 [ICorDebugDataTarget：： GetPlatform](icordebugdatatarget-getplatform-method.md) 方法所指定的電腦類型。</span><span class="sxs-lookup"><span data-stu-id="f1f00-112">On Windows platforms, `pContext` must be a `CONTEXT` structure (defined in WinNT.h) that is appropriate for the machine type specified by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="f1f00-113">`contextFlags` 的值必須與 `ContextFlags` 結構的欄位相同 `CONTEXT` 。</span><span class="sxs-lookup"><span data-stu-id="f1f00-113">`contextFlags` must have the same values as the `ContextFlags` field of the `CONTEXT` structure.</span></span> <span data-ttu-id="f1f00-114">`CONTEXT`結構是處理器特定的; 如需詳細資料，請參閱 WinNT .h 檔案。</span><span class="sxs-lookup"><span data-stu-id="f1f00-114">The `CONTEXT` structure is processor-specific; refer to the WinNT.h file for details.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1f00-115">需求</span><span class="sxs-lookup"><span data-stu-id="f1f00-115">Requirements</span></span>  

 <span data-ttu-id="f1f00-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f1f00-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1f00-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f1f00-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1f00-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1f00-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1f00-119">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1f00-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1f00-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1f00-120">See also</span></span>

- [<span data-ttu-id="f1f00-121">ICorDebugDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="f1f00-121">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="f1f00-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="f1f00-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f1f00-123">偵錯</span><span class="sxs-lookup"><span data-stu-id="f1f00-123">Debugging</span></span>](index.md)
