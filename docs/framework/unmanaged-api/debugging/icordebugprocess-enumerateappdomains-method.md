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
ms.openlocfilehash: 748a44075f7f73e54bab689bcb8865dee2b14946
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207832"
---
# <a name="icordebugprocessenumerateappdomains-method"></a><span data-ttu-id="ba905-102">ICorDebugProcess::EnumerateAppDomains 方法</span><span class="sxs-lookup"><span data-stu-id="ba905-102">ICorDebugProcess::EnumerateAppDomains Method</span></span>
<span data-ttu-id="ba905-103">列舉這個進程中的所有應用程式域。</span><span class="sxs-lookup"><span data-stu-id="ba905-103">Enumerates all the application domains in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba905-104">語法</span><span class="sxs-lookup"><span data-stu-id="ba905-104">Syntax</span></span>  
  
``` cpp
HRESULT EnumerateAppDomains(  
    [out] ICorDebugAppDomainEnum **ppAppDomains);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba905-105">參數</span><span class="sxs-lookup"><span data-stu-id="ba905-105">Parameters</span></span>  
 `ppAppDomains`  
 <span data-ttu-id="ba905-106">脫銷[ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md)位址的指標，此為此進程中應用程式域的列舉值。</span><span class="sxs-lookup"><span data-stu-id="ba905-106">[out] A pointer to the address of an [ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md) that is an enumerator for the application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba905-107">備註</span><span class="sxs-lookup"><span data-stu-id="ba905-107">Remarks</span></span>  
 <span data-ttu-id="ba905-108">這個方法可以在[ICorDebugManagedCallback：： CreateProcess](icordebugmanagedcallback-createprocess-method.md)回呼之前使用。</span><span class="sxs-lookup"><span data-stu-id="ba905-108">This method can be used before the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba905-109">需求</span><span class="sxs-lookup"><span data-stu-id="ba905-109">Requirements</span></span>  
 <span data-ttu-id="ba905-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ba905-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba905-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba905-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba905-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba905-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba905-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba905-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
