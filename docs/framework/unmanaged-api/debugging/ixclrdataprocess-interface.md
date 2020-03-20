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
ms.openlocfilehash: e7e53615e38d0ab76f9e7c0a753be3c13780057d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178368"
---
# <a name="ixclrdataprocess-interface"></a><span data-ttu-id="29100-102">IXCLRDataProcess 介面</span><span class="sxs-lookup"><span data-stu-id="29100-102">IXCLRDataProcess Interface</span></span>

<span data-ttu-id="29100-103">提供了查詢有關進程的資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="29100-103">Provides methods for querying information about a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="29100-104">方法</span><span class="sxs-lookup"><span data-stu-id="29100-104">Methods</span></span>

| <span data-ttu-id="29100-105">方法</span><span class="sxs-lookup"><span data-stu-id="29100-105">Method</span></span>                                                                                                                                               | <span data-ttu-id="29100-106">描述</span><span class="sxs-lookup"><span data-stu-id="29100-106">Description</span></span>                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="29100-107">GetAppDomainByUniqueId</span><span class="sxs-lookup"><span data-stu-id="29100-107">GetAppDomainByUniqueId</span></span>](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | <span data-ttu-id="29100-108">通過進程`AppDomain`的唯一 ID 獲取 進程中的 。</span><span class="sxs-lookup"><span data-stu-id="29100-108">Gets an `AppDomain` in a process by its unique id.</span></span>                                              |
| [<span data-ttu-id="29100-109">StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="29100-109">StartEnumModules</span></span>](ixclrdataprocess-startenummodules-method.md)                                   | <span data-ttu-id="29100-110">提供一個控制碼來枚舉進程的模組。</span><span class="sxs-lookup"><span data-stu-id="29100-110">Provides a handle to enumerate the modules of a process.</span></span>                                        |
| [<span data-ttu-id="29100-111">EnumModule</span><span class="sxs-lookup"><span data-stu-id="29100-111">EnumModule</span></span>](ixclrdataprocess-enummodule-method.md)                                               | <span data-ttu-id="29100-112">枚舉此過程的模組。</span><span class="sxs-lookup"><span data-stu-id="29100-112">Enumerates the modules of this process.</span></span>                                                         |
| [<span data-ttu-id="29100-113">EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="29100-113">EndEnumModules</span></span>](ixclrdataprocess-endenummodules-method.md)                                       | <span data-ttu-id="29100-114">釋放模組枚舉期間使用的內部反覆運算器使用的資源。</span><span class="sxs-lookup"><span data-stu-id="29100-114">Releases the resources used by internal iterators used during module enumeration.</span></span>               |
| [<span data-ttu-id="29100-115">StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="29100-115">StartEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | <span data-ttu-id="29100-116">提供一個控制碼來枚舉從給定位址`AppDomain`開始的方法實例。</span><span class="sxs-lookup"><span data-stu-id="29100-116">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span> |
| [<span data-ttu-id="29100-117">EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="29100-117">EnumMethodInstanceByAddress</span></span>](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | <span data-ttu-id="29100-118">枚舉從位址偏移開始此過程的方法實例。</span><span class="sxs-lookup"><span data-stu-id="29100-118">Enumerates the method instances of this process starting at an address offset.</span></span>                  |
| [<span data-ttu-id="29100-119">EndEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="29100-119">EndEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | <span data-ttu-id="29100-120">釋放實例枚舉期間使用的內部反覆運算器使用的資源。</span><span class="sxs-lookup"><span data-stu-id="29100-120">Releases the resources used by internal iterators used during instance enumeration.</span></span>             |

## <a name="remarks"></a><span data-ttu-id="29100-121">備註</span><span class="sxs-lookup"><span data-stu-id="29100-121">Remarks</span></span>

<span data-ttu-id="29100-122">此介面位於運行時內，不會通過任何標頭或庫檔公開。</span><span class="sxs-lookup"><span data-stu-id="29100-122">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="29100-123">但是，它是一個 COM 介面，派生自`IUnknown`GUID，`5c552ab6-fc09-4cb3-8e36-22fa03c798b7`可通過通常的 COM 機制獲得。</span><span class="sxs-lookup"><span data-stu-id="29100-123">However, it's a COM interface that derives from `IUnknown` with GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="29100-124">需求</span><span class="sxs-lookup"><span data-stu-id="29100-124">Requirements</span></span>

<span data-ttu-id="29100-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="29100-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>
<span data-ttu-id="29100-126">**標題：** 沒有</span><span class="sxs-lookup"><span data-stu-id="29100-126">**Header:** None</span></span>  
<span data-ttu-id="29100-127">**庫：** 沒有</span><span class="sxs-lookup"><span data-stu-id="29100-127">**Library:** None</span></span>  
<span data-ttu-id="29100-128">**.NET 框架版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="29100-128">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="29100-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29100-129">See also</span></span>

- [<span data-ttu-id="29100-130">偵錯</span><span class="sxs-lookup"><span data-stu-id="29100-130">Debugging</span></span>](index.md)
- [<span data-ttu-id="29100-131">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="29100-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
