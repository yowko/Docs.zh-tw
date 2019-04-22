---
title: ICoreClrDebugTarget::EnumProcesses 方法
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumProcesses
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumProcesses
helpviewer_keywords:
- remote debugging API [Silverlight]
- EnumProcesses method, ICorClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::EnumProcesses method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: e00fd477-4f49-43d3-bd0e-3094824b1136
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a35f5ff62ca37337b7becb023f2328cbe05aea6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59216037"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a><span data-ttu-id="0b459-102">ICoreClrDebugTarget::EnumProcesses 方法</span><span class="sxs-lookup"><span data-stu-id="0b459-102">ICoreClrDebugTarget::EnumProcesses Method</span></span>
<span data-ttu-id="0b459-103">列舉在遠端電腦上執行的處理序。</span><span class="sxs-lookup"><span data-stu-id="0b459-103">Enumerates the processes that are running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b459-104">語法</span><span class="sxs-lookup"><span data-stu-id="0b459-104">Syntax</span></span>  
  
```  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,   
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b459-105">參數</span><span class="sxs-lookup"><span data-stu-id="0b459-105">Parameters</span></span>  
 `pcProcs`  
 <span data-ttu-id="0b459-106">[out] `ppProcs` 中傳回的處理序數目。</span><span class="sxs-lookup"><span data-stu-id="0b459-106">[out] The number of processes returned in `ppProcs`.</span></span> <span data-ttu-id="0b459-107">這個值可以是 0 (零)。</span><span class="sxs-lookup"><span data-stu-id="0b459-107">This value can be 0 (zero).</span></span>  
  
 `ppProcs`  
 <span data-ttu-id="0b459-108">[out]陣列[CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)代表在遠端電腦上執行的處理程序的結構。</span><span class="sxs-lookup"><span data-stu-id="0b459-108">[out] An array of [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) structures that represent the processes running on the remote computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b459-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="0b459-109">Return Value</span></span>  
 <span data-ttu-id="0b459-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0b459-110">S_OK</span></span>  
 <span data-ttu-id="0b459-111">成功。</span><span class="sxs-lookup"><span data-stu-id="0b459-111">Success.</span></span>  
  
 <span data-ttu-id="0b459-112">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0b459-112">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="0b459-113">無法為 `ppProcs` 配置足夠的記憶體。</span><span class="sxs-lookup"><span data-stu-id="0b459-113">Unable to allocate enough memory for `ppProcs`.</span></span>  
  
 <span data-ttu-id="0b459-114">E_FAIL (或其他 E_ 傳回碼)</span><span class="sxs-lookup"><span data-stu-id="0b459-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="0b459-115">其他失敗。</span><span class="sxs-lookup"><span data-stu-id="0b459-115">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b459-116">備註</span><span class="sxs-lookup"><span data-stu-id="0b459-116">Remarks</span></span>  
 <span data-ttu-id="0b459-117">若要釋放這個方法所配置的記憶體，請呼叫[icoreclrdebugtarget:: Freememory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="0b459-117">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b459-118">需求</span><span class="sxs-lookup"><span data-stu-id="0b459-118">Requirements</span></span>  
 <span data-ttu-id="0b459-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0b459-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b459-120">**標頭：** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="0b459-120">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="0b459-121">**程式庫：** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="0b459-121">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="0b459-122">**.NET framework 版本：** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="0b459-122">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b459-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b459-123">See also</span></span>

- [<span data-ttu-id="0b459-124">ICoreClrDebugTarget 介面</span><span class="sxs-lookup"><span data-stu-id="0b459-124">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
