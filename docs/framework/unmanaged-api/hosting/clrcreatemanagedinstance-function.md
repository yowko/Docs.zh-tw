---
title: "ClrCreateManagedInstance 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ClrCreateManagedInstance
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- ClrCreateManagedInstance
helpviewer_keywords:
- ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 64a1bc6bbd89e3a36ac53b322bb246a7e61baa67
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="clrcreatemanagedinstance-function"></a><span data-ttu-id="b48dd-102">ClrCreateManagedInstance 函式</span><span class="sxs-lookup"><span data-stu-id="b48dd-102">ClrCreateManagedInstance Function</span></span>
<span data-ttu-id="b48dd-103">建立指定的 managed 型別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b48dd-103">Creates an instance of the specified managed type.</span></span>  
  
 <span data-ttu-id="b48dd-104">此函式中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b48dd-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="b48dd-105">若要建立的 managed 類型中，執行個體使用 COM 啟用，或使用裝載 (請參閱[CLR 裝載介面中加入.NET Framework 4 和 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md))。</span><span class="sxs-lookup"><span data-stu-id="b48dd-105">Use COM activation to create an instance of the managed type, or use hosting (see [CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b48dd-106">語法</span><span class="sxs-lookup"><span data-stu-id="b48dd-106">Syntax</span></span>  
  
```  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,   
    [in]  REFIID   riid,   
    [out] void     **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b48dd-107">參數</span><span class="sxs-lookup"><span data-stu-id="b48dd-107">Parameters</span></span>  
 `pTypeName`  
 <span data-ttu-id="b48dd-108">[in]所要求的執行個體類型的名稱指標。</span><span class="sxs-lookup"><span data-stu-id="b48dd-108">[in] A pointer to the name of the instance type being requested.</span></span>  
  
 `riid`  
 <span data-ttu-id="b48dd-109">[in]`IID`所要求的執行個體型別。</span><span class="sxs-lookup"><span data-stu-id="b48dd-109">[in] The `IID` of the instance type being requested.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="b48dd-110">[out]指標的指標，呼叫者所要求之 managed 型別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b48dd-110">[out] A pointer to a pointer to an instance of the managed type that was requested by the caller.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b48dd-111">備註</span><span class="sxs-lookup"><span data-stu-id="b48dd-111">Remarks</span></span>  
 <span data-ttu-id="b48dd-112">Common language runtime 已應載入處理序。</span><span class="sxs-lookup"><span data-stu-id="b48dd-112">The common language runtime should already be loaded into a process.</span></span> <span data-ttu-id="b48dd-113">例如，藉由呼叫載入[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)函式之前`ClrCreateManagedInstance`呼叫函式。</span><span class="sxs-lookup"><span data-stu-id="b48dd-113">For example, it can be loaded by using a call to the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function before the `ClrCreateManagedInstance` function is called.</span></span> <span data-ttu-id="b48dd-114">如果未載入執行階段，`ClrCreateManagedInstance`第一次嘗試載入的執行階段 v1.0.3705。</span><span class="sxs-lookup"><span data-stu-id="b48dd-114">If the runtime is not loaded, `ClrCreateManagedInstance` first tries to load v1.0.3705 of the runtime.</span></span> <span data-ttu-id="b48dd-115">如果失敗，它會嘗試載入執行階段的最新版本。</span><span class="sxs-lookup"><span data-stu-id="b48dd-115">If that fails, it attempts to load the latest version of the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b48dd-116">需求</span><span class="sxs-lookup"><span data-stu-id="b48dd-116">Requirements</span></span>  
 <span data-ttu-id="b48dd-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b48dd-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b48dd-118">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b48dd-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b48dd-119">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b48dd-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b48dd-120">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b48dd-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b48dd-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="b48dd-121">See Also</span></span>  
 [<span data-ttu-id="b48dd-122">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="b48dd-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
 [<span data-ttu-id="b48dd-123">裝載</span><span class="sxs-lookup"><span data-stu-id="b48dd-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
