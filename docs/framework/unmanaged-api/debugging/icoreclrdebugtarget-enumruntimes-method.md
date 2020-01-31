---
title: ICoreClrDebugTarget::EnumRuntimes 方法
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumRuntimes
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumRuntimes
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget::EnumRuntimes method [Silverlight debugging]
- EnumRuntimes method, ICoreClrDebugTarget interface [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 316df866-442d-40cc-b049-45e8adcb65d1
topic_type:
- apiref
ms.openlocfilehash: 4b55ac1d895bfecbe74be447bd06f4aa22b9d04f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790786"
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a><span data-ttu-id="2372d-102">ICoreClrDebugTarget::EnumRuntimes 方法</span><span class="sxs-lookup"><span data-stu-id="2372d-102">ICoreClrDebugTarget::EnumRuntimes Method</span></span>
<span data-ttu-id="2372d-103">列舉遠端電腦上所執行之指定處理序中的 Common Language Runtime (CLR)。</span><span class="sxs-lookup"><span data-stu-id="2372d-103">Enumerates the common language runtimes (CLRs) in the specified process that is running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2372d-104">語法</span><span class="sxs-lookup"><span data-stu-id="2372d-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="2372d-105">參數</span><span class="sxs-lookup"><span data-stu-id="2372d-105">Parameters</span></span>  
 `dwInternalProcessID`  
 <span data-ttu-id="2372d-106">[in] 要列舉執行階段之處理序的內部處理序 ID。</span><span class="sxs-lookup"><span data-stu-id="2372d-106">[in] The internal process ID of the process for which you want to enumerate runtimes.</span></span> <span data-ttu-id="2372d-107">這會從對應的[CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md)`m_dwInternalID`。</span><span class="sxs-lookup"><span data-stu-id="2372d-107">This will be `m_dwInternalID` from the corresponding [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md).</span></span>  
  
 `pcRuntimes`  
 <span data-ttu-id="2372d-108">[out] `ppRuntimes` 中傳回的執行階段數目。</span><span class="sxs-lookup"><span data-stu-id="2372d-108">[out] The number of runtimes returned in `ppRuntimes`.</span></span> <span data-ttu-id="2372d-109">這個值可以是 0 (零)。</span><span class="sxs-lookup"><span data-stu-id="2372d-109">This value can be 0 (zero).</span></span>  
  
 `ppRuntimes`  
 <span data-ttu-id="2372d-110">脫銷[CoreClrDebugRuntimeInfo](coreclrdebugruntimeinfo-structure.md)結構的陣列，代表在遠端目標進程中載入的執行時間。</span><span class="sxs-lookup"><span data-stu-id="2372d-110">[out] An array of [CoreClrDebugRuntimeInfo](coreclrdebugruntimeinfo-structure.md) structures that represent the runtimes loaded in the remote target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2372d-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="2372d-111">Return Value</span></span>  
 <span data-ttu-id="2372d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="2372d-112">S_OK</span></span>  
 <span data-ttu-id="2372d-113">成功。</span><span class="sxs-lookup"><span data-stu-id="2372d-113">Success.</span></span>  
  
 <span data-ttu-id="2372d-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="2372d-114">S_FALSE</span></span>  
 <span data-ttu-id="2372d-115">`dwInternalProcessID` 不符合電腦上所執行的任何處理序，可能是因為處理序已終止。</span><span class="sxs-lookup"><span data-stu-id="2372d-115">`dwInternalProcessID` does not match any process that is running on the computer, probably because the process was terminated.</span></span> <span data-ttu-id="2372d-116">`pcRuntimes` 和 `ppRuntimes` 將為 null。</span><span class="sxs-lookup"><span data-stu-id="2372d-116">`pcRuntimes` and `ppRuntimes` will be null.</span></span>  
  
 <span data-ttu-id="2372d-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="2372d-117">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="2372d-118">無法為 `ppRuntimes` 配置足夠的記憶體。</span><span class="sxs-lookup"><span data-stu-id="2372d-118">Unable to allocate enough memory for `ppRuntimes`.</span></span>  
  
 <span data-ttu-id="2372d-119">E_FAIL (或其他 E_ 傳回碼)</span><span class="sxs-lookup"><span data-stu-id="2372d-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="2372d-120">其他失敗。</span><span class="sxs-lookup"><span data-stu-id="2372d-120">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2372d-121">備註</span><span class="sxs-lookup"><span data-stu-id="2372d-121">Remarks</span></span>  
 <span data-ttu-id="2372d-122">若要釋放這個方法所配置的記憶體，請呼叫[ICoreClrDebugTarget：： FreeMemory](icoreclrdebugtarget-freememory-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="2372d-122">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2372d-123">需求</span><span class="sxs-lookup"><span data-stu-id="2372d-123">Requirements</span></span>  
 <span data-ttu-id="2372d-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2372d-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2372d-125">**標頭：** CoreClrRemoteDebuggingInterfaces。h</span><span class="sxs-lookup"><span data-stu-id="2372d-125">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="2372d-126">連結**庫：** mscordbi_macx86 .dll</span><span class="sxs-lookup"><span data-stu-id="2372d-126">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="2372d-127">**.NET Framework 版本：** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="2372d-127">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2372d-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="2372d-128">See also</span></span>

- [<span data-ttu-id="2372d-129">ICoreClrDebugTarget 介面</span><span class="sxs-lookup"><span data-stu-id="2372d-129">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)
