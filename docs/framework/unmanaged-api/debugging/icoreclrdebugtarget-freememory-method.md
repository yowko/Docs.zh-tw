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
ms.openlocfilehash: 1e159cacd297d56d63e512643ec4d3fe0c3709c0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95694397"
---
# <a name="icoreclrdebugtargetfreememory-method"></a><span data-ttu-id="59940-102">ICoreClrDebugTarget::FreeMemory 方法</span><span class="sxs-lookup"><span data-stu-id="59940-102">ICoreClrDebugTarget::FreeMemory Method</span></span>

<span data-ttu-id="59940-103">釋放 [ICoreClrDebugTarget：： EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) 和 [ICoreClrDebugTarget：： EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md) 方法所配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="59940-103">Frees the memory allocated by the [ICoreClrDebugTarget::EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) and [ICoreClrDebugTarget::EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md) methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59940-104">語法</span><span class="sxs-lookup"><span data-stu-id="59940-104">Syntax</span></span>  
  
```cpp  
void FreeMemory (  
     [in] void*pMemory);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59940-105">參數</span><span class="sxs-lookup"><span data-stu-id="59940-105">Parameters</span></span>  

 `pMemory`  
 <span data-ttu-id="59940-106">在 [ICoreClrDebugTarget：： EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) 或 [ICoreClrDebugTarget：： EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md) 方法所傳回之陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="59940-106">[in] A pointer to the array that is returned by either the [ICoreClrDebugTarget::EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) or the [ICoreClrDebugTarget::EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59940-107">需求</span><span class="sxs-lookup"><span data-stu-id="59940-107">Requirements</span></span>  

 <span data-ttu-id="59940-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="59940-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59940-109">**標頭：** CoreClrRemoteDebuggingInterfaces。h</span><span class="sxs-lookup"><span data-stu-id="59940-109">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="59940-110">連結 **庫：** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="59940-110">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="59940-111">**.NET Framework 版本：** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="59940-111">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59940-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59940-112">See also</span></span>

- [<span data-ttu-id="59940-113">ICoreClrDebugTarget 介面</span><span class="sxs-lookup"><span data-stu-id="59940-113">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)
