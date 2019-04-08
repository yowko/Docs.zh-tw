---
title: ICLRDataTarget::GetCurrentThreadID 方法
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetCurrentThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::GetCurrentThreadID method [.NET Framework debugging]
ms.assetid: dc9a0a6c-d592-4fb7-86ed-62684da3b0e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9687f6139d67a2387091367c2c72167e03be4eee
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080653"
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a><span data-ttu-id="92df7-102">ICLRDataTarget::GetCurrentThreadID 方法</span><span class="sxs-lookup"><span data-stu-id="92df7-102">ICLRDataTarget::GetCurrentThreadID Method</span></span>
<span data-ttu-id="92df7-103">取得目前執行緒的作業系統識別項。</span><span class="sxs-lookup"><span data-stu-id="92df7-103">Gets the operating system identifier for the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92df7-104">語法</span><span class="sxs-lookup"><span data-stu-id="92df7-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92df7-105">參數</span><span class="sxs-lookup"><span data-stu-id="92df7-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="92df7-106">[out]目標處理序的目前執行緒的作業系統識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="92df7-106">[out] A pointer to the operating system identifier of the current thread for the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92df7-107">備註</span><span class="sxs-lookup"><span data-stu-id="92df7-107">Remarks</span></span>  
 <span data-ttu-id="92df7-108">如果沒有目前的執行緒，目標處理序`GetCurrentThreadID`方法可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="92df7-108">If there is no current thread for the target process, the `GetCurrentThreadID` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92df7-109">需求</span><span class="sxs-lookup"><span data-stu-id="92df7-109">Requirements</span></span>  
 <span data-ttu-id="92df7-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="92df7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92df7-111">**標頭：** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="92df7-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="92df7-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92df7-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="92df7-113">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="92df7-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="92df7-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92df7-114">See also</span></span>

- [<span data-ttu-id="92df7-115">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="92df7-115">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
