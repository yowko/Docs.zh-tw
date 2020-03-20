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
ms.openlocfilehash: 7fbe0cf3e93d75749fa3f463f3f97dbd1bfe27a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176535"
---
# <a name="clrcreatemanagedinstance-function"></a><span data-ttu-id="9ecf7-102">ClrCreateManagedInstance 函式</span><span class="sxs-lookup"><span data-stu-id="9ecf7-102">ClrCreateManagedInstance Function</span></span>
<span data-ttu-id="9ecf7-103">創建指定託管類型的實例。</span><span class="sxs-lookup"><span data-stu-id="9ecf7-103">Creates an instance of the specified managed type.</span></span>  
  
 <span data-ttu-id="9ecf7-104">此功能已在 .NET 框架 4 中棄用。</span><span class="sxs-lookup"><span data-stu-id="9ecf7-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="9ecf7-105">使用 COM 啟動創建託管類型的實例，或使用託管（請參閱[在 .NET 框架 4 和 4.5 中添加的 CLR 託管介面](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)）。</span><span class="sxs-lookup"><span data-stu-id="9ecf7-105">Use COM activation to create an instance of the managed type, or use hosting (see [CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ecf7-106">語法</span><span class="sxs-lookup"><span data-stu-id="9ecf7-106">Syntax</span></span>  
  
```cpp  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,
    [in]  REFIID   riid,
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ecf7-107">參數</span><span class="sxs-lookup"><span data-stu-id="9ecf7-107">Parameters</span></span>  
 `pTypeName`  
 <span data-ttu-id="9ecf7-108">[在]指向要請求的實例類型的名稱的指標。</span><span class="sxs-lookup"><span data-stu-id="9ecf7-108">[in] A pointer to the name of the instance type being requested.</span></span>  
  
 `riid`  
 <span data-ttu-id="9ecf7-109">[在]要`IID`請求的實例類型的 。</span><span class="sxs-lookup"><span data-stu-id="9ecf7-109">[in] The `IID` of the instance type being requested.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="9ecf7-110">[出]指向調用方請求的託管類型的實例的指標。</span><span class="sxs-lookup"><span data-stu-id="9ecf7-110">[out] A pointer to a pointer to an instance of the managed type that was requested by the caller.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ecf7-111">備註</span><span class="sxs-lookup"><span data-stu-id="9ecf7-111">Remarks</span></span>  
 <span data-ttu-id="9ecf7-112">公共語言運行時應已載入到進程中。</span><span class="sxs-lookup"><span data-stu-id="9ecf7-112">The common language runtime should already be loaded into a process.</span></span> <span data-ttu-id="9ecf7-113">例如，在調用`ClrCreateManagedInstance`函數之前，可以使用對[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)函數的調用來載入它。</span><span class="sxs-lookup"><span data-stu-id="9ecf7-113">For example, it can be loaded by using a call to the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function before the `ClrCreateManagedInstance` function is called.</span></span> <span data-ttu-id="9ecf7-114">如果未載入運行時，`ClrCreateManagedInstance`則首先嘗試載入運行時的 v1.0.3705。</span><span class="sxs-lookup"><span data-stu-id="9ecf7-114">If the runtime is not loaded, `ClrCreateManagedInstance` first tries to load v1.0.3705 of the runtime.</span></span> <span data-ttu-id="9ecf7-115">如果失敗，它將嘗試載入最新版本的運行時。</span><span class="sxs-lookup"><span data-stu-id="9ecf7-115">If that fails, it attempts to load the latest version of the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ecf7-116">需求</span><span class="sxs-lookup"><span data-stu-id="9ecf7-116">Requirements</span></span>  
 <span data-ttu-id="9ecf7-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9ecf7-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ecf7-118">**標題：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9ecf7-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9ecf7-119">**庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9ecf7-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ecf7-120">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ecf7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ecf7-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ecf7-121">See also</span></span>

- [<span data-ttu-id="9ecf7-122">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="9ecf7-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="9ecf7-123">裝載</span><span class="sxs-lookup"><span data-stu-id="9ecf7-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
