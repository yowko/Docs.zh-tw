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
ms.openlocfilehash: cdf5776e1ac9907e63aba0e0d400e48aff683d51
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785292"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a><span data-ttu-id="beaa6-102">ICLRDataTarget::SetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="beaa6-102">ICLRDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="beaa6-103">設定目標進程中指定之執行緒的目前內容。</span><span class="sxs-lookup"><span data-stu-id="beaa6-103">Sets the current context of the specified thread in the target process.</span></span> <span data-ttu-id="beaa6-104">這個方法是由 common language runtime （CLR）資料存取服務呼叫。</span><span class="sxs-lookup"><span data-stu-id="beaa6-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="beaa6-105">語法</span><span class="sxs-lookup"><span data-stu-id="beaa6-105">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]   
         BYTE               *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="beaa6-106">參數</span><span class="sxs-lookup"><span data-stu-id="beaa6-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="beaa6-107">在目標進程中線程的作業系統識別碼。</span><span class="sxs-lookup"><span data-stu-id="beaa6-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="beaa6-108">在內容的大小。</span><span class="sxs-lookup"><span data-stu-id="beaa6-108">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="beaa6-109">在包含內容之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="beaa6-109">[in] Pointer to a buffer containing the context.</span></span>  
  
 <span data-ttu-id="beaa6-110">`context` 緩衝區中的資料將會採用 Win32 `CONTEXT` 結構的格式。</span><span class="sxs-lookup"><span data-stu-id="beaa6-110">The data in the `context` buffer will be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="beaa6-111">內容會指定處理器特定的暫存器資料，因此 Win32 `CONTEXT` 結構的定義取決於處理器的架構。</span><span class="sxs-lookup"><span data-stu-id="beaa6-111">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="beaa6-112">如需 Win32 `CONTEXT` 結構的定義，請參閱 WinNT 標頭檔。</span><span class="sxs-lookup"><span data-stu-id="beaa6-112">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="beaa6-113">備註</span><span class="sxs-lookup"><span data-stu-id="beaa6-113">Remarks</span></span>  
 <span data-ttu-id="beaa6-114">此方法是由偵錯應用程式的作者來實作。</span><span class="sxs-lookup"><span data-stu-id="beaa6-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="beaa6-115">需求</span><span class="sxs-lookup"><span data-stu-id="beaa6-115">Requirements</span></span>  
 <span data-ttu-id="beaa6-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="beaa6-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="beaa6-117">**標頭：** ClrData .idl，ClrData。h</span><span class="sxs-lookup"><span data-stu-id="beaa6-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="beaa6-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="beaa6-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="beaa6-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="beaa6-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beaa6-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="beaa6-120">See also</span></span>

- [<span data-ttu-id="beaa6-121">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="beaa6-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
