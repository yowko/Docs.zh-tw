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
ms.openlocfilehash: 4e672030ae83b57da6f9ab66630513d79f28b8f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131994"
---
# <a name="clrcreatemanagedinstance-function"></a><span data-ttu-id="62955-102">ClrCreateManagedInstance 函式</span><span class="sxs-lookup"><span data-stu-id="62955-102">ClrCreateManagedInstance Function</span></span>
<span data-ttu-id="62955-103">建立指定之 managed 類型的實例。</span><span class="sxs-lookup"><span data-stu-id="62955-103">Creates an instance of the specified managed type.</span></span>  
  
 <span data-ttu-id="62955-104">此函式在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="62955-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="62955-105">使用 COM 啟動來建立 managed 類型的實例，或使用裝載（請參閱[在 .NET Framework 4 和4.5 中新增的 CLR 裝載介面](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)）。</span><span class="sxs-lookup"><span data-stu-id="62955-105">Use COM activation to create an instance of the managed type, or use hosting (see [CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62955-106">語法</span><span class="sxs-lookup"><span data-stu-id="62955-106">Syntax</span></span>  
  
```cpp  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,   
    [in]  REFIID   riid,   
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62955-107">參數</span><span class="sxs-lookup"><span data-stu-id="62955-107">Parameters</span></span>  
 `pTypeName`  
 <span data-ttu-id="62955-108">在所要求之實例類型名稱的指標。</span><span class="sxs-lookup"><span data-stu-id="62955-108">[in] A pointer to the name of the instance type being requested.</span></span>  
  
 `riid`  
 <span data-ttu-id="62955-109">在所要求之實例類型的 `IID`。</span><span class="sxs-lookup"><span data-stu-id="62955-109">[in] The `IID` of the instance type being requested.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="62955-110">脫銷呼叫端所要求之 managed 型別的實例指標。</span><span class="sxs-lookup"><span data-stu-id="62955-110">[out] A pointer to a pointer to an instance of the managed type that was requested by the caller.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62955-111">備註</span><span class="sxs-lookup"><span data-stu-id="62955-111">Remarks</span></span>  
 <span data-ttu-id="62955-112">通用語言執行平臺應該已經載入進程中。</span><span class="sxs-lookup"><span data-stu-id="62955-112">The common language runtime should already be loaded into a process.</span></span> <span data-ttu-id="62955-113">例如，您可以在呼叫 `ClrCreateManagedInstance` 函式之前，使用[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)函數的呼叫來載入它。</span><span class="sxs-lookup"><span data-stu-id="62955-113">For example, it can be loaded by using a call to the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function before the `ClrCreateManagedInstance` function is called.</span></span> <span data-ttu-id="62955-114">如果未載入執行時間，`ClrCreateManagedInstance` 會先嘗試載入執行時間的 v v1.0.3705。</span><span class="sxs-lookup"><span data-stu-id="62955-114">If the runtime is not loaded, `ClrCreateManagedInstance` first tries to load v1.0.3705 of the runtime.</span></span> <span data-ttu-id="62955-115">如果失敗，則會嘗試載入最新版本的執行時間。</span><span class="sxs-lookup"><span data-stu-id="62955-115">If that fails, it attempts to load the latest version of the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62955-116">需求</span><span class="sxs-lookup"><span data-stu-id="62955-116">Requirements</span></span>  
 <span data-ttu-id="62955-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="62955-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62955-118">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="62955-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="62955-119">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="62955-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="62955-120">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62955-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62955-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="62955-121">See also</span></span>

- [<span data-ttu-id="62955-122">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="62955-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="62955-123">裝載</span><span class="sxs-lookup"><span data-stu-id="62955-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
