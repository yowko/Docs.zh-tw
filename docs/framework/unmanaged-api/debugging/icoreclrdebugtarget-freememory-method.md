---
title: "ICoreClrDebugTarget::FreeMemory 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICoreDebugTarget.FreeMemory
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: ICoreClrDebugTarget::FreeMemory
helpviewer_keywords:
- remote debugging API [Silverlight]
- FreeMemory method, ICoreClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::FreeMemory method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 98f2a0db-a6ec-4f9b-861d-f82485237d08
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2079d0363e962d0423623c7c0261cc64fc4b3237
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icoreclrdebugtargetfreememory-method"></a><span data-ttu-id="78fdd-102">ICoreClrDebugTarget::FreeMemory 方法</span><span class="sxs-lookup"><span data-stu-id="78fdd-102">ICoreClrDebugTarget::FreeMemory Method</span></span>
<span data-ttu-id="78fdd-103">釋放所配置的記憶體[icoreclrdebugtarget:: Enumprocesses](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md)和[icoreclrdebugtarget:: Enumruntimes](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="78fdd-103">Frees the memory allocated by the [ICoreClrDebugTarget::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md) and [ICoreClrDebugTarget::EnumRuntimes](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md) methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78fdd-104">語法</span><span class="sxs-lookup"><span data-stu-id="78fdd-104">Syntax</span></span>  
  
```  
void FreeMemory (  
     [in] void*pMemory);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78fdd-105">參數</span><span class="sxs-lookup"><span data-stu-id="78fdd-105">Parameters</span></span>  
 `pMemory`  
 <span data-ttu-id="78fdd-106">[in]傳回由陣列的指標[icoreclrdebugtarget:: Enumprocesses](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md)或[icoreclrdebugtarget:: Enumruntimes](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="78fdd-106">[in] A pointer to the array that is returned by either the [ICoreClrDebugTarget::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md) or the [ICoreClrDebugTarget::EnumRuntimes](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78fdd-107">需求</span><span class="sxs-lookup"><span data-stu-id="78fdd-107">Requirements</span></span>  
 <span data-ttu-id="78fdd-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="78fdd-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78fdd-109">**標頭：** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="78fdd-109">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="78fdd-110">**程式庫：** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="78fdd-110">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="78fdd-111">**.NET framework 版本：** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="78fdd-111">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78fdd-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="78fdd-112">See Also</span></span>  
 [<span data-ttu-id="78fdd-113">ICoreClrDebugTarget 介面</span><span class="sxs-lookup"><span data-stu-id="78fdd-113">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
