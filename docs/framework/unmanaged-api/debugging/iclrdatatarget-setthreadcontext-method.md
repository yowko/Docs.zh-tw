---
title: ICLRDataTarget::SetThreadContext 方法
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::SetThreadContext
helpviewer_keywords:
- SetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::SetThreadContext method [.NET Framework debugging]
ms.assetid: 103c8502-81fe-40d7-9c1e-9008d8fb19e1
topic_type:
- apiref
ms.openlocfilehash: c135c051637858682c22db58d562e1d50eea562b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723697"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a><span data-ttu-id="21630-102">ICLRDataTarget::SetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="21630-102">ICLRDataTarget::SetThreadContext Method</span></span>

<span data-ttu-id="21630-103">在目標進程中，設定指定之執行緒的目前內容。</span><span class="sxs-lookup"><span data-stu-id="21630-103">Sets the current context of the specified thread in the target process.</span></span> <span data-ttu-id="21630-104">Common language runtime (CLR) 資料存取服務會呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="21630-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21630-105">語法</span><span class="sxs-lookup"><span data-stu-id="21630-105">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]
         BYTE               *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21630-106">參數</span><span class="sxs-lookup"><span data-stu-id="21630-106">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="21630-107">在目標進程中線程的作業系統識別碼。</span><span class="sxs-lookup"><span data-stu-id="21630-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="21630-108">在內容的大小。</span><span class="sxs-lookup"><span data-stu-id="21630-108">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="21630-109">在包含內容之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="21630-109">[in] Pointer to a buffer containing the context.</span></span>  
  
 <span data-ttu-id="21630-110">緩衝區中的資料 `context` 將採用 Win32 結構的格式 `CONTEXT` 。</span><span class="sxs-lookup"><span data-stu-id="21630-110">The data in the `context` buffer will be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="21630-111">內容會指定處理器特定的登錄資料，因此 Win32 結構的定義 `CONTEXT` 取決於處理器的架構。</span><span class="sxs-lookup"><span data-stu-id="21630-111">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="21630-112">請參閱 WinNT 標頭檔中的 Win32 `CONTEXT` 結構定義。</span><span class="sxs-lookup"><span data-stu-id="21630-112">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21630-113">備註</span><span class="sxs-lookup"><span data-stu-id="21630-113">Remarks</span></span>  

 <span data-ttu-id="21630-114">此方法是由偵錯應用程式的作者來實作。</span><span class="sxs-lookup"><span data-stu-id="21630-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21630-115">需求</span><span class="sxs-lookup"><span data-stu-id="21630-115">Requirements</span></span>  

 <span data-ttu-id="21630-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="21630-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21630-117">**標頭：** ClrData .idl、ClrData。h</span><span class="sxs-lookup"><span data-stu-id="21630-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="21630-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21630-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21630-119">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21630-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21630-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21630-120">See also</span></span>

- [<span data-ttu-id="21630-121">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="21630-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
