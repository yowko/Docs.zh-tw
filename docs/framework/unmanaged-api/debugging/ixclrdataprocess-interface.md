---
title: IXCLRDataProcess 介面
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess Interface
helpviewer.keywords:
- IXCLRDataProcess Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 6a6def8fc10f04b89aa8d8c735025b01f9b6ddfb
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420756"
---
# <a name="ixclrdataprocess-interface"></a><span data-ttu-id="223d7-102">IXCLRDataProcess 介面</span><span class="sxs-lookup"><span data-stu-id="223d7-102">IXCLRDataProcess Interface</span></span>

<span data-ttu-id="223d7-103">提供查詢處理常式相關資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="223d7-103">Provides methods for querying information about a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="223d7-104">方法</span><span class="sxs-lookup"><span data-stu-id="223d7-104">Methods</span></span>

| <span data-ttu-id="223d7-105">方法</span><span class="sxs-lookup"><span data-stu-id="223d7-105">Method</span></span>                                                                                                                                               | <span data-ttu-id="223d7-106">描述</span><span class="sxs-lookup"><span data-stu-id="223d7-106">Description</span></span>                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="223d7-107">GetAppDomainByUniqueId</span><span class="sxs-lookup"><span data-stu-id="223d7-107">GetAppDomainByUniqueId</span></span>](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | <span data-ttu-id="223d7-108">`AppDomain`依其唯一識別碼取得處理常式中的。</span><span class="sxs-lookup"><span data-stu-id="223d7-108">Gets an `AppDomain` in a process by its unique id.</span></span>                                              |
| [<span data-ttu-id="223d7-109">StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="223d7-109">StartEnumModules</span></span>](ixclrdataprocess-startenummodules-method.md)                                   | <span data-ttu-id="223d7-110">提供列舉進程模組的控制碼。</span><span class="sxs-lookup"><span data-stu-id="223d7-110">Provides a handle to enumerate the modules of a process.</span></span>                                        |
| [<span data-ttu-id="223d7-111">EnumModule</span><span class="sxs-lookup"><span data-stu-id="223d7-111">EnumModule</span></span>](ixclrdataprocess-enummodule-method.md)                                               | <span data-ttu-id="223d7-112">列舉此進程的模組。</span><span class="sxs-lookup"><span data-stu-id="223d7-112">Enumerates the modules of this process.</span></span>                                                         |
| [<span data-ttu-id="223d7-113">EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="223d7-113">EndEnumModules</span></span>](ixclrdataprocess-endenummodules-method.md)                                       | <span data-ttu-id="223d7-114">釋放模組列舉期間所使用之內部反覆運算器所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="223d7-114">Releases the resources used by internal iterators used during module enumeration.</span></span>               |
| [<span data-ttu-id="223d7-115">StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="223d7-115">StartEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | <span data-ttu-id="223d7-116">提供一個控制碼，用來列舉 `AppDomain` 從指定位址開始的方法實例。</span><span class="sxs-lookup"><span data-stu-id="223d7-116">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span> |
| [<span data-ttu-id="223d7-117">EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="223d7-117">EnumMethodInstanceByAddress</span></span>](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | <span data-ttu-id="223d7-118">從位址位移開始，列舉這個進程的方法實例。</span><span class="sxs-lookup"><span data-stu-id="223d7-118">Enumerates the method instances of this process starting at an address offset.</span></span>                  |
| [<span data-ttu-id="223d7-119">EndEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="223d7-119">EndEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | <span data-ttu-id="223d7-120">釋放實例列舉期間所使用之內部反覆運算器所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="223d7-120">Releases the resources used by internal iterators used during instance enumeration.</span></span>             |

## <a name="remarks"></a><span data-ttu-id="223d7-121">備註</span><span class="sxs-lookup"><span data-stu-id="223d7-121">Remarks</span></span>

<span data-ttu-id="223d7-122">這個介面存在於執行時間內，而且不會透過任何標頭或程式庫檔案公開。</span><span class="sxs-lookup"><span data-stu-id="223d7-122">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="223d7-123">不過，它是衍生自的 COM 介面，其 `IUnknown` 具有 `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` 可透過一般 COM 機制取得的 GUID。</span><span class="sxs-lookup"><span data-stu-id="223d7-123">However, it's a COM interface that derives from `IUnknown` with GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="223d7-124">需求</span><span class="sxs-lookup"><span data-stu-id="223d7-124">Requirements</span></span>

<span data-ttu-id="223d7-125">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="223d7-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="223d7-126">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="223d7-126">**Header:** None</span></span>  
<span data-ttu-id="223d7-127">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="223d7-127">**Library:** None</span></span>  
<span data-ttu-id="223d7-128">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="223d7-128">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="223d7-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="223d7-129">See also</span></span>

- [<span data-ttu-id="223d7-130">偵錯</span><span class="sxs-lookup"><span data-stu-id="223d7-130">Debugging</span></span>](index.md)
- [<span data-ttu-id="223d7-131">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="223d7-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
