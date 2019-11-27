---
title: ICorProfilerCallback::AppDomainCreationFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationFinished
helpviewer_keywords:
- AppDomainCreationFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationFinished method [.NET Framework profiling]
ms.assetid: dbab7d90-d515-4dc9-8195-294d5d04bab6
topic_type:
- apiref
ms.openlocfilehash: eaf0ae2a1b86234495c1804cff8b74331b3e8021
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445283"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="bfdb2-102">ICorProfilerCallback::AppDomainCreationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="bfdb2-102">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>
<span data-ttu-id="bfdb2-103">通知分析工具已建立應用程式域。</span><span class="sxs-lookup"><span data-stu-id="bfdb2-103">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfdb2-104">語法</span><span class="sxs-lookup"><span data-stu-id="bfdb2-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);   
```  
  
## <a name="parameters"></a><span data-ttu-id="bfdb2-105">參數</span><span class="sxs-lookup"><span data-stu-id="bfdb2-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="bfdb2-106">在識別已建立的網域。</span><span class="sxs-lookup"><span data-stu-id="bfdb2-106">[in] Identifies the domain which has been created.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="bfdb2-107">在HRESULT，指出是否已順利完成建立應用程式網域。</span><span class="sxs-lookup"><span data-stu-id="bfdb2-107">[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bfdb2-108">備註</span><span class="sxs-lookup"><span data-stu-id="bfdb2-108">Remarks</span></span>  
 <span data-ttu-id="bfdb2-109">在呼叫 `AppDomainCreationFinished` 方法之前，應用程式識別碼對任何資訊要求而言都是不正確。</span><span class="sxs-lookup"><span data-stu-id="bfdb2-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="bfdb2-110">載入應用程式域的某些部分可能會在 `AppDomainCreationFinished` 回呼之後繼續進行。</span><span class="sxs-lookup"><span data-stu-id="bfdb2-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="bfdb2-111">`hrStatus` 中的失敗 HRESULT 表示失敗。</span><span class="sxs-lookup"><span data-stu-id="bfdb2-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="bfdb2-112">不過，`hrStatus` 中的成功 HRESULT 只會指出建立應用程式域的第一個部分已成功。</span><span class="sxs-lookup"><span data-stu-id="bfdb2-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfdb2-113">需求</span><span class="sxs-lookup"><span data-stu-id="bfdb2-113">Requirements</span></span>  
 <span data-ttu-id="bfdb2-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bfdb2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfdb2-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bfdb2-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bfdb2-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bfdb2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bfdb2-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfdb2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfdb2-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bfdb2-118">See also</span></span>

- [<span data-ttu-id="bfdb2-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="bfdb2-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
