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
ms.openlocfilehash: 45a409bda8861701e68d3ea1a956a4c35ce88ddd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738789"
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a><span data-ttu-id="89a65-102">ICLRDataTarget::GetCurrentThreadID 方法</span><span class="sxs-lookup"><span data-stu-id="89a65-102">ICLRDataTarget::GetCurrentThreadID Method</span></span>
<span data-ttu-id="89a65-103">取得目前執行緒的作業系統識別項。</span><span class="sxs-lookup"><span data-stu-id="89a65-103">Gets the operating system identifier for the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89a65-104">語法</span><span class="sxs-lookup"><span data-stu-id="89a65-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89a65-105">參數</span><span class="sxs-lookup"><span data-stu-id="89a65-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="89a65-106">[out]目標處理序的目前執行緒的作業系統識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="89a65-106">[out] A pointer to the operating system identifier of the current thread for the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89a65-107">備註</span><span class="sxs-lookup"><span data-stu-id="89a65-107">Remarks</span></span>  
 <span data-ttu-id="89a65-108">如果沒有目前的執行緒，目標處理序`GetCurrentThreadID`方法可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="89a65-108">If there is no current thread for the target process, the `GetCurrentThreadID` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89a65-109">需求</span><span class="sxs-lookup"><span data-stu-id="89a65-109">Requirements</span></span>  
 <span data-ttu-id="89a65-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="89a65-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89a65-111">**標頭：** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="89a65-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="89a65-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89a65-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89a65-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89a65-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89a65-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89a65-114">See also</span></span>

- [<span data-ttu-id="89a65-115">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="89a65-115">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
