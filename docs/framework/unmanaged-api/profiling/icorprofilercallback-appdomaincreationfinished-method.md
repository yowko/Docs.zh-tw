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
ms.openlocfilehash: 76f56971223154d3ed966c272081049adf30de54
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500490"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="d48b9-102">ICorProfilerCallback::AppDomainCreationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="d48b9-102">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>
<span data-ttu-id="d48b9-103">通知分析工具已建立應用程式域。</span><span class="sxs-lookup"><span data-stu-id="d48b9-103">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d48b9-104">語法</span><span class="sxs-lookup"><span data-stu-id="d48b9-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);
```  
  
## <a name="parameters"></a><span data-ttu-id="d48b9-105">參數</span><span class="sxs-lookup"><span data-stu-id="d48b9-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="d48b9-106">\[在中，識別已建立的網域。</span><span class="sxs-lookup"><span data-stu-id="d48b9-106">\[in] Identifies the domain which has been created.</span></span>

- `hrStatus`

  <span data-ttu-id="d48b9-107">\[中的 HRESULT，指出應用程式域的建立是否已順利完成。</span><span class="sxs-lookup"><span data-stu-id="d48b9-107">\[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="d48b9-108">備註</span><span class="sxs-lookup"><span data-stu-id="d48b9-108">Remarks</span></span>  
 <span data-ttu-id="d48b9-109">在呼叫方法之前，應用程式識別碼對任何資訊要求而言都是不正確 `AppDomainCreationFinished` 。</span><span class="sxs-lookup"><span data-stu-id="d48b9-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="d48b9-110">載入應用程式域的某些部分可能會在回呼之後繼續進行 `AppDomainCreationFinished` 。</span><span class="sxs-lookup"><span data-stu-id="d48b9-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="d48b9-111">中的失敗 HRESULT `hrStatus` 表示失敗。</span><span class="sxs-lookup"><span data-stu-id="d48b9-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="d48b9-112">不過，中的成功 HRESULT `hrStatus` 只會指出建立應用程式域的第一個部分已成功。</span><span class="sxs-lookup"><span data-stu-id="d48b9-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d48b9-113">規格需求</span><span class="sxs-lookup"><span data-stu-id="d48b9-113">Requirements</span></span>  
 <span data-ttu-id="d48b9-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d48b9-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d48b9-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d48b9-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d48b9-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d48b9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d48b9-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d48b9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d48b9-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d48b9-118">See also</span></span>

- [<span data-ttu-id="d48b9-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="d48b9-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
