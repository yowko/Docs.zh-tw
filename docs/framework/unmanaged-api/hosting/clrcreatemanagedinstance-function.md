---
title: ClrCreateManagedInstance 函式
ms.date: 03/30/2017
api_name:
- ClrCreateManagedInstance
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- ClrCreateManagedInstance
helpviewer_keywords:
- ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f82303a3d38e7a5baaf1c3edcc41518228360d34
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59088453"
---
# <a name="clrcreatemanagedinstance-function"></a><span data-ttu-id="07a09-102">ClrCreateManagedInstance 函式</span><span class="sxs-lookup"><span data-stu-id="07a09-102">ClrCreateManagedInstance Function</span></span>
<span data-ttu-id="07a09-103">建立指定之 managed 型別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="07a09-103">Creates an instance of the specified managed type.</span></span>  
  
 <span data-ttu-id="07a09-104">此函式中的過時[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="07a09-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="07a09-105">若要建立的 managed 類型中，執行個體中使用 COM 啟動，或使用裝載 (請參閱[CLR 裝載介面中加入.NET Framework 4 和 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md))。</span><span class="sxs-lookup"><span data-stu-id="07a09-105">Use COM activation to create an instance of the managed type, or use hosting (see [CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07a09-106">語法</span><span class="sxs-lookup"><span data-stu-id="07a09-106">Syntax</span></span>  
  
```  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,   
    [in]  REFIID   riid,   
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07a09-107">參數</span><span class="sxs-lookup"><span data-stu-id="07a09-107">Parameters</span></span>  
 `pTypeName`  
 <span data-ttu-id="07a09-108">[in]所要求的執行個體類型的名稱指標。</span><span class="sxs-lookup"><span data-stu-id="07a09-108">[in] A pointer to the name of the instance type being requested.</span></span>  
  
 `riid`  
 <span data-ttu-id="07a09-109">[in]`IID`所要求的執行個體類型。</span><span class="sxs-lookup"><span data-stu-id="07a09-109">[in] The `IID` of the instance type being requested.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="07a09-110">[out]指標的指標，呼叫端所要求之 managed 型別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="07a09-110">[out] A pointer to a pointer to an instance of the managed type that was requested by the caller.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07a09-111">備註</span><span class="sxs-lookup"><span data-stu-id="07a09-111">Remarks</span></span>  
 <span data-ttu-id="07a09-112">Common language runtime 已應載入的程序。</span><span class="sxs-lookup"><span data-stu-id="07a09-112">The common language runtime should already be loaded into a process.</span></span> <span data-ttu-id="07a09-113">例如，藉由呼叫載入[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)函式之前`ClrCreateManagedInstance`呼叫函式。</span><span class="sxs-lookup"><span data-stu-id="07a09-113">For example, it can be loaded by using a call to the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function before the `ClrCreateManagedInstance` function is called.</span></span> <span data-ttu-id="07a09-114">如果未載入執行階段，`ClrCreateManagedInstance`第一次嘗試載入 v1.0.3705 的執行階段。</span><span class="sxs-lookup"><span data-stu-id="07a09-114">If the runtime is not loaded, `ClrCreateManagedInstance` first tries to load v1.0.3705 of the runtime.</span></span> <span data-ttu-id="07a09-115">如果失敗，它會嘗試載入的執行階段的最新版本。</span><span class="sxs-lookup"><span data-stu-id="07a09-115">If that fails, it attempts to load the latest version of the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07a09-116">需求</span><span class="sxs-lookup"><span data-stu-id="07a09-116">Requirements</span></span>  
 <span data-ttu-id="07a09-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="07a09-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07a09-118">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="07a09-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="07a09-119">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="07a09-119">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="07a09-120">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="07a09-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="07a09-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07a09-121">See also</span></span>

- [<span data-ttu-id="07a09-122">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="07a09-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="07a09-123">裝載</span><span class="sxs-lookup"><span data-stu-id="07a09-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
