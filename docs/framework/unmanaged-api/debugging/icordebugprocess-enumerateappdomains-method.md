---
title: ICorDebugProcess::EnumerateAppDomains 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.EnumerateAppDomains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::EnumerateAppDomains
helpviewer_keywords:
- ICorDebugProcess::EnumerateAppDomains method [.NET Framework debugging]
- EnumerateAppDomains method [.NET Framework debugging]
ms.assetid: d508981f-e2b2-445b-a649-69951c22702d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 02e051d311e447475bea724b0bd7420ee8b590f6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57495724"
---
# <a name="icordebugprocessenumerateappdomains-method"></a><span data-ttu-id="310bb-102">ICorDebugProcess::EnumerateAppDomains 方法</span><span class="sxs-lookup"><span data-stu-id="310bb-102">ICorDebugProcess::EnumerateAppDomains Method</span></span>
<span data-ttu-id="310bb-103">列舉在此程序中的所有應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="310bb-103">Enumerates all the application domains in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="310bb-104">語法</span><span class="sxs-lookup"><span data-stu-id="310bb-104">Syntax</span></span>  
  
```  
HRESULT EnumerateAppDomains(  
    [out] ICorDebugAppDomainEnum **ppAppDomains);  
```  
  
## <a name="parameters"></a><span data-ttu-id="310bb-105">參數</span><span class="sxs-lookup"><span data-stu-id="310bb-105">Parameters</span></span>  
 `ppAppDomains`  
 <span data-ttu-id="310bb-106">[out]位址指標[ICorDebugAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md)也就是在此程序中的應用程式定義域的列舉值。</span><span class="sxs-lookup"><span data-stu-id="310bb-106">[out] A pointer to the address of an [ICorDebugAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md) that is an enumerator for the application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="310bb-107">備註</span><span class="sxs-lookup"><span data-stu-id="310bb-107">Remarks</span></span>  
 <span data-ttu-id="310bb-108">之前，可以使用這個方法[icordebugmanagedcallback:: Createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="310bb-108">This method can be used before the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="310bb-109">需求</span><span class="sxs-lookup"><span data-stu-id="310bb-109">Requirements</span></span>  
 <span data-ttu-id="310bb-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="310bb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="310bb-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="310bb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="310bb-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="310bb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="310bb-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="310bb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
