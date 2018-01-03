---
title: "ICorDebugProcess::EnumerateAppDomains 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.EnumerateAppDomains
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::EnumerateAppDomains
helpviewer_keywords:
- ICorDebugProcess::EnumerateAppDomains method [.NET Framework debugging]
- EnumerateAppDomains method [.NET Framework debugging]
ms.assetid: d508981f-e2b2-445b-a649-69951c22702d
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0ba0f554a4ddf52b7c4ced1658055c4370f112ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessenumerateappdomains-method"></a><span data-ttu-id="04757-102">ICorDebugProcess::EnumerateAppDomains 方法</span><span class="sxs-lookup"><span data-stu-id="04757-102">ICorDebugProcess::EnumerateAppDomains Method</span></span>
<span data-ttu-id="04757-103">列舉此程序中的所有應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="04757-103">Enumerates all the application domains in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04757-104">語法</span><span class="sxs-lookup"><span data-stu-id="04757-104">Syntax</span></span>  
  
```  
HRESULT EnumerateAppDomains(  
    [out] ICorDebugAppDomainEnum **ppAppDomains);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="04757-105">參數</span><span class="sxs-lookup"><span data-stu-id="04757-105">Parameters</span></span>  
 `ppAppDomains`  
 <span data-ttu-id="04757-106">[out]位址指標[ICorDebugAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md)也就是這個處理序中的應用程式定義域的列舉值。</span><span class="sxs-lookup"><span data-stu-id="04757-106">[out] A pointer to the address of an [ICorDebugAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md) that is an enumerator for the application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04757-107">備註</span><span class="sxs-lookup"><span data-stu-id="04757-107">Remarks</span></span>  
 <span data-ttu-id="04757-108">之前，可以使用這個方法[icordebugmanagedcallback:: Createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="04757-108">This method can be used before the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04757-109">需求</span><span class="sxs-lookup"><span data-stu-id="04757-109">Requirements</span></span>  
 <span data-ttu-id="04757-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="04757-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04757-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="04757-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04757-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04757-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04757-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04757-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
