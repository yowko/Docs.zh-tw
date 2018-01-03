---
title: "ICoreClrDebugTarget::EnumProcesses 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICoreClrDebugTarget.EnumProcesses
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: ICoreClrDebugTarget::EnumProcesses
helpviewer_keywords:
- remote debugging API [Silverlight]
- EnumProcesses method, ICorClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::EnumProcesses method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: e00fd477-4f49-43d3-bd0e-3094824b1136
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8296b4b137032400ee172b6d3670bc1a53dbe60d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a><span data-ttu-id="b98d7-102">ICoreClrDebugTarget::EnumProcesses 方法</span><span class="sxs-lookup"><span data-stu-id="b98d7-102">ICoreClrDebugTarget::EnumProcesses Method</span></span>
<span data-ttu-id="b98d7-103">列舉在遠端電腦上執行的處理序。</span><span class="sxs-lookup"><span data-stu-id="b98d7-103">Enumerates the processes that are running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b98d7-104">語法</span><span class="sxs-lookup"><span data-stu-id="b98d7-104">Syntax</span></span>  
  
```  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,   
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b98d7-105">參數</span><span class="sxs-lookup"><span data-stu-id="b98d7-105">Parameters</span></span>  
 `pcProcs`  
 <span data-ttu-id="b98d7-106">[out] `ppProcs` 中傳回的處理序數目。</span><span class="sxs-lookup"><span data-stu-id="b98d7-106">[out] The number of processes returned in `ppProcs`.</span></span> <span data-ttu-id="b98d7-107">這個值可以是 0 (零)。</span><span class="sxs-lookup"><span data-stu-id="b98d7-107">This value can be 0 (zero).</span></span>  
  
 `ppProcs`  
 <span data-ttu-id="b98d7-108">[out]陣列[CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) ，此結構表示遠端電腦上執行的處理程序。</span><span class="sxs-lookup"><span data-stu-id="b98d7-108">[out] An array of [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) structures that represent the processes running on the remote computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b98d7-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="b98d7-109">Return Value</span></span>  
 <span data-ttu-id="b98d7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b98d7-110">S_OK</span></span>  
 <span data-ttu-id="b98d7-111">成功。</span><span class="sxs-lookup"><span data-stu-id="b98d7-111">Success.</span></span>  
  
 <span data-ttu-id="b98d7-112">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b98d7-112">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="b98d7-113">無法為 `ppProcs` 配置足夠的記憶體。</span><span class="sxs-lookup"><span data-stu-id="b98d7-113">Unable to allocate enough memory for `ppProcs`.</span></span>  
  
 <span data-ttu-id="b98d7-114">E_FAIL (或其他 E_ 傳回碼)</span><span class="sxs-lookup"><span data-stu-id="b98d7-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="b98d7-115">其他失敗。</span><span class="sxs-lookup"><span data-stu-id="b98d7-115">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b98d7-116">備註</span><span class="sxs-lookup"><span data-stu-id="b98d7-116">Remarks</span></span>  
 <span data-ttu-id="b98d7-117">若要釋放由這個方法所配置的記憶體，請呼叫[icoreclrdebugtarget:: Freememory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="b98d7-117">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b98d7-118">需求</span><span class="sxs-lookup"><span data-stu-id="b98d7-118">Requirements</span></span>  
 <span data-ttu-id="b98d7-119">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b98d7-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b98d7-120">**標頭：** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="b98d7-120">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="b98d7-121">**程式庫：** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="b98d7-121">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="b98d7-122">**.NET framework 版本：** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="b98d7-122">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b98d7-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="b98d7-123">See Also</span></span>  
 [<span data-ttu-id="b98d7-124">ICoreClrDebugTarget 介面</span><span class="sxs-lookup"><span data-stu-id="b98d7-124">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
