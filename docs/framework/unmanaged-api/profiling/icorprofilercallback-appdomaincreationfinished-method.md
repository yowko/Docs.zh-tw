---
title: "ICorProfilerCallback::AppDomainCreationFinished 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AppDomainCreationFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AppDomainCreationFinished
helpviewer_keywords:
- AppDomainCreationFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationFinished method [.NET Framework profiling]
ms.assetid: dbab7d90-d515-4dc9-8195-294d5d04bab6
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f779e5a7b0b38558593e84c26b33784383765ca0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="29944-102">ICorProfilerCallback::AppDomainCreationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="29944-102">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>
<span data-ttu-id="29944-103">通知分析工具已建立應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="29944-103">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29944-104">語法</span><span class="sxs-lookup"><span data-stu-id="29944-104">Syntax</span></span>  
  
```  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="29944-105">參數</span><span class="sxs-lookup"><span data-stu-id="29944-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="29944-106">[in]識別已建立的網域。</span><span class="sxs-lookup"><span data-stu-id="29944-106">[in] Identifies the domain which has been created.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="29944-107">[in]HRESULT，指出是否已成功完成建立應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="29944-107">[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29944-108">備註</span><span class="sxs-lookup"><span data-stu-id="29944-108">Remarks</span></span>  
 <span data-ttu-id="29944-109">應用程式識別碼不是有效的任何資訊要求到`AppDomainCreationFinished`方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="29944-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="29944-110">載入應用程式定義域的某些部分可能會繼續之後`AppDomainCreationFinished`回呼。</span><span class="sxs-lookup"><span data-stu-id="29944-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="29944-111">失敗的 HRESULT 中`hrStatus`表示失敗。</span><span class="sxs-lookup"><span data-stu-id="29944-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="29944-112">不過，成功 HRESULT 中`hrStatus`只會指出已成功建立應用程式定義域的第一個部分。</span><span class="sxs-lookup"><span data-stu-id="29944-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29944-113">需求</span><span class="sxs-lookup"><span data-stu-id="29944-113">Requirements</span></span>  
 <span data-ttu-id="29944-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="29944-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29944-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="29944-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="29944-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29944-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29944-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29944-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29944-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="29944-118">See Also</span></span>  
 [<span data-ttu-id="29944-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="29944-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
