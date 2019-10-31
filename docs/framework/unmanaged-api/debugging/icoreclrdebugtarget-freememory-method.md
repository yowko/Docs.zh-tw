---
title: ICoreClrDebugTarget::FreeMemory 方法
ms.date: 03/30/2017
api_name:
- ICoreDebugTarget.FreeMemory
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::FreeMemory
helpviewer_keywords:
- remote debugging API [Silverlight]
- FreeMemory method, ICoreClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::FreeMemory method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 98f2a0db-a6ec-4f9b-861d-f82485237d08
topic_type:
- apiref
ms.openlocfilehash: 6821aacb80726cf202c99428a401b53b5c6ee566
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121802"
---
# <a name="icoreclrdebugtargetfreememory-method"></a><span data-ttu-id="ecb7c-102">ICoreClrDebugTarget::FreeMemory 方法</span><span class="sxs-lookup"><span data-stu-id="ecb7c-102">ICoreClrDebugTarget::FreeMemory Method</span></span>
<span data-ttu-id="ecb7c-103">釋放[ICoreClrDebugTarget：： EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md)和[ICoreClrDebugTarget：： EnumRuntimes](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md)方法所配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="ecb7c-103">Frees the memory allocated by the [ICoreClrDebugTarget::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md) and [ICoreClrDebugTarget::EnumRuntimes](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md) methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecb7c-104">語法</span><span class="sxs-lookup"><span data-stu-id="ecb7c-104">Syntax</span></span>  
  
```cpp  
void FreeMemory (  
     [in] void*pMemory);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ecb7c-105">參數</span><span class="sxs-lookup"><span data-stu-id="ecb7c-105">Parameters</span></span>  
 `pMemory`  
 <span data-ttu-id="ecb7c-106">在由[ICoreClrDebugTarget：： EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md)或[ICoreClrDebugTarget：： EnumRuntimes](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md)方法所傳回之陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="ecb7c-106">[in] A pointer to the array that is returned by either the [ICoreClrDebugTarget::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md) or the [ICoreClrDebugTarget::EnumRuntimes](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecb7c-107">需求</span><span class="sxs-lookup"><span data-stu-id="ecb7c-107">Requirements</span></span>  
 <span data-ttu-id="ecb7c-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ecb7c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecb7c-109">**標頭：** CoreClrRemoteDebuggingInterfaces。h</span><span class="sxs-lookup"><span data-stu-id="ecb7c-109">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="ecb7c-110">連結**庫：** mscordbi_macx86</span><span class="sxs-lookup"><span data-stu-id="ecb7c-110">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="ecb7c-111">**.NET Framework 版本：** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="ecb7c-111">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecb7c-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="ecb7c-112">See also</span></span>

- [<span data-ttu-id="ecb7c-113">ICoreClrDebugTarget 介面</span><span class="sxs-lookup"><span data-stu-id="ecb7c-113">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
