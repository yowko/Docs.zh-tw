---
title: ICLRDataTarget::GetThreadContext 方法
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetThreadContext
helpviewer_keywords:
- ICLRDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: b9d8c3b5-3a2e-4225-95d4-dd052c4532c3
topic_type:
- apiref
ms.openlocfilehash: 35b7bff5d4d778a429ddc1dcd0206e6e8970ee4f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703495"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a><span data-ttu-id="775f9-102">ICLRDataTarget::GetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="775f9-102">ICLRDataTarget::GetThreadContext Method</span></span>

<span data-ttu-id="775f9-103">取得目標進程中指定執行緒的目前執行內容。</span><span class="sxs-lookup"><span data-stu-id="775f9-103">Gets the current execution context for the given thread in the target process.</span></span> <span data-ttu-id="775f9-104">Common language runtime 資料存取服務會呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="775f9-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="775f9-105">語法</span><span class="sxs-lookup"><span data-stu-id="775f9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="775f9-106">參數</span><span class="sxs-lookup"><span data-stu-id="775f9-106">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="775f9-107">在目標進程中線程的作業系統識別碼。</span><span class="sxs-lookup"><span data-stu-id="775f9-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="775f9-108">在旗標，指定要傳回內容中的哪些部分。</span><span class="sxs-lookup"><span data-stu-id="775f9-108">[in] Flags that specify which parts of the context to return.</span></span> <span data-ttu-id="775f9-109">此實作為會傳回至少內容的這些部分。</span><span class="sxs-lookup"><span data-stu-id="775f9-109">The implementation will return at least these parts of the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="775f9-110">在內容的大小。</span><span class="sxs-lookup"><span data-stu-id="775f9-110">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="775f9-111">擴展要放置內容的緩衝區指標。</span><span class="sxs-lookup"><span data-stu-id="775f9-111">[out] Pointer to a buffer in which to place the context.</span></span>  
  
 <span data-ttu-id="775f9-112">緩衝區中的資料 `context` 必須採用 Win32 結構的格式 `CONTEXT` 。</span><span class="sxs-lookup"><span data-stu-id="775f9-112">The data in the `context` buffer must be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="775f9-113">內容會指定處理器特定的登錄資料，因此 Win32 結構的定義 `CONTEXT` 取決於處理器的架構。</span><span class="sxs-lookup"><span data-stu-id="775f9-113">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="775f9-114">請參閱 WinNT 標頭檔中的 Win32 `CONTEXT` 結構定義。</span><span class="sxs-lookup"><span data-stu-id="775f9-114">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="775f9-115">備註</span><span class="sxs-lookup"><span data-stu-id="775f9-115">Remarks</span></span>  

 <span data-ttu-id="775f9-116">此方法是由偵錯應用程式的作者來實作。</span><span class="sxs-lookup"><span data-stu-id="775f9-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="775f9-117">需求</span><span class="sxs-lookup"><span data-stu-id="775f9-117">Requirements</span></span>  

 <span data-ttu-id="775f9-118">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="775f9-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="775f9-119">**標頭：** ClrData .idl、ClrData。h</span><span class="sxs-lookup"><span data-stu-id="775f9-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="775f9-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="775f9-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="775f9-121">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="775f9-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="775f9-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="775f9-122">See also</span></span>

- [<span data-ttu-id="775f9-123">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="775f9-123">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
