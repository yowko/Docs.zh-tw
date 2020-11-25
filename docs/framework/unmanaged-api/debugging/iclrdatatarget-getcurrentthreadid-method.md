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
ms.openlocfilehash: 3a355822710394e9351f10be78dea283e2e9907c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703586"
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a><span data-ttu-id="2d2ea-102">ICLRDataTarget::GetCurrentThreadID 方法</span><span class="sxs-lookup"><span data-stu-id="2d2ea-102">ICLRDataTarget::GetCurrentThreadID Method</span></span>

<span data-ttu-id="2d2ea-103">取得目前線程的作業系統識別碼。</span><span class="sxs-lookup"><span data-stu-id="2d2ea-103">Gets the operating system identifier for the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d2ea-104">語法</span><span class="sxs-lookup"><span data-stu-id="2d2ea-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d2ea-105">參數</span><span class="sxs-lookup"><span data-stu-id="2d2ea-105">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="2d2ea-106">擴展目標進程之目前線程的作業系統識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="2d2ea-106">[out] A pointer to the operating system identifier of the current thread for the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d2ea-107">備註</span><span class="sxs-lookup"><span data-stu-id="2d2ea-107">Remarks</span></span>  

 <span data-ttu-id="2d2ea-108">如果目標進程沒有目前的執行緒， `GetCurrentThreadID` 方法可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="2d2ea-108">If there is no current thread for the target process, the `GetCurrentThreadID` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d2ea-109">需求</span><span class="sxs-lookup"><span data-stu-id="2d2ea-109">Requirements</span></span>  

 <span data-ttu-id="2d2ea-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2d2ea-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d2ea-111">**標頭：** ClrData .idl、ClrData。h</span><span class="sxs-lookup"><span data-stu-id="2d2ea-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="2d2ea-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d2ea-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d2ea-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d2ea-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d2ea-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d2ea-114">See also</span></span>

- [<span data-ttu-id="2d2ea-115">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="2d2ea-115">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
