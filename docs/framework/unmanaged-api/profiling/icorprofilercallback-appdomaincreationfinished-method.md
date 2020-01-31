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
ms.openlocfilehash: 1cf3f2b62b388b6c2d6fcd75b1b07a67d5b2e49f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866698"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="2c91d-102">ICorProfilerCallback::AppDomainCreationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="2c91d-102">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>
<span data-ttu-id="2c91d-103">通知分析工具已建立應用程式域。</span><span class="sxs-lookup"><span data-stu-id="2c91d-103">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c91d-104">語法</span><span class="sxs-lookup"><span data-stu-id="2c91d-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);   
```  
  
## <a name="parameters"></a><span data-ttu-id="2c91d-105">參數</span><span class="sxs-lookup"><span data-stu-id="2c91d-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="2c91d-106">中的 \[] 可識別已建立的網域。</span><span class="sxs-lookup"><span data-stu-id="2c91d-106">\[in] Identifies the domain which has been created.</span></span>

- `hrStatus`

  <span data-ttu-id="2c91d-107">\[in]） HRESULT，指出應用程式域的建立是否已順利完成。</span><span class="sxs-lookup"><span data-stu-id="2c91d-107">\[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="2c91d-108">備註</span><span class="sxs-lookup"><span data-stu-id="2c91d-108">Remarks</span></span>  
 <span data-ttu-id="2c91d-109">在呼叫 `AppDomainCreationFinished` 方法之前，應用程式識別碼對任何資訊要求而言都是不正確。</span><span class="sxs-lookup"><span data-stu-id="2c91d-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="2c91d-110">載入應用程式域的某些部分可能會在 `AppDomainCreationFinished` 回呼之後繼續進行。</span><span class="sxs-lookup"><span data-stu-id="2c91d-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="2c91d-111">`hrStatus` 中的失敗 HRESULT 表示失敗。</span><span class="sxs-lookup"><span data-stu-id="2c91d-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="2c91d-112">不過，`hrStatus` 中的成功 HRESULT 只會指出建立應用程式域的第一個部分已成功。</span><span class="sxs-lookup"><span data-stu-id="2c91d-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c91d-113">需求</span><span class="sxs-lookup"><span data-stu-id="2c91d-113">Requirements</span></span>  
 <span data-ttu-id="2c91d-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2c91d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c91d-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2c91d-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2c91d-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c91d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c91d-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c91d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c91d-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="2c91d-118">See also</span></span>

- [<span data-ttu-id="2c91d-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="2c91d-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
