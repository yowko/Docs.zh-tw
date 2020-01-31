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
ms.openlocfilehash: 35e3e37b1487b5dda9945402c6a3338384147f9a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792632"
---
# <a name="icordebugprocessenumerateappdomains-method"></a><span data-ttu-id="bde5f-102">ICorDebugProcess::EnumerateAppDomains 方法</span><span class="sxs-lookup"><span data-stu-id="bde5f-102">ICorDebugProcess::EnumerateAppDomains Method</span></span>
<span data-ttu-id="bde5f-103">列舉這個進程中的所有應用程式域。</span><span class="sxs-lookup"><span data-stu-id="bde5f-103">Enumerates all the application domains in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bde5f-104">語法</span><span class="sxs-lookup"><span data-stu-id="bde5f-104">Syntax</span></span>  
  
``` cpp 
HRESULT EnumerateAppDomains(  
    [out] ICorDebugAppDomainEnum **ppAppDomains);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bde5f-105">參數</span><span class="sxs-lookup"><span data-stu-id="bde5f-105">Parameters</span></span>  
 `ppAppDomains`  
 <span data-ttu-id="bde5f-106">脫銷[ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md)位址的指標，此為此進程中應用程式域的列舉值。</span><span class="sxs-lookup"><span data-stu-id="bde5f-106">[out] A pointer to the address of an [ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md) that is an enumerator for the application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bde5f-107">備註</span><span class="sxs-lookup"><span data-stu-id="bde5f-107">Remarks</span></span>  
 <span data-ttu-id="bde5f-108">這個方法可以在[ICorDebugManagedCallback：： CreateProcess](icordebugmanagedcallback-createprocess-method.md)回呼之前使用。</span><span class="sxs-lookup"><span data-stu-id="bde5f-108">This method can be used before the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bde5f-109">需求</span><span class="sxs-lookup"><span data-stu-id="bde5f-109">Requirements</span></span>  
 <span data-ttu-id="bde5f-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bde5f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bde5f-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bde5f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bde5f-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bde5f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bde5f-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bde5f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
