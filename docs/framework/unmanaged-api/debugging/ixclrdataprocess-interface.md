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
ms.openlocfilehash: 376ec2b840bc17c79ed1f27c17a8ddd22c37a0f4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96245337"
---
# <a name="ixclrdataprocess-interface"></a><span data-ttu-id="fd55c-102">IXCLRDataProcess 介面</span><span class="sxs-lookup"><span data-stu-id="fd55c-102">IXCLRDataProcess Interface</span></span>

<span data-ttu-id="fd55c-103">提供查詢進程相關資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="fd55c-103">Provides methods for querying information about a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="fd55c-104">方法</span><span class="sxs-lookup"><span data-stu-id="fd55c-104">Methods</span></span>

| <span data-ttu-id="fd55c-105">方法</span><span class="sxs-lookup"><span data-stu-id="fd55c-105">Method</span></span>                                                                                                                                               | <span data-ttu-id="fd55c-106">描述</span><span class="sxs-lookup"><span data-stu-id="fd55c-106">Description</span></span>                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="fd55c-107">GetRuntimeNameByAddress</span><span class="sxs-lookup"><span data-stu-id="fd55c-107">GetRuntimeNameByAddress</span></span>](ixclrdataprocess-getruntimenamebyaddress-method.md)                     | <span data-ttu-id="fd55c-108">取得指定位址的名稱。</span><span class="sxs-lookup"><span data-stu-id="fd55c-108">Gets a name for the given address.</span></span>                                                               |
| [<span data-ttu-id="fd55c-109">GetAppDomainByUniqueId</span><span class="sxs-lookup"><span data-stu-id="fd55c-109">GetAppDomainByUniqueId</span></span>](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | <span data-ttu-id="fd55c-110">`AppDomain`依其唯一識別碼取得進程中的。</span><span class="sxs-lookup"><span data-stu-id="fd55c-110">Gets an `AppDomain` in a process by its unique id.</span></span>                                              |
| [<span data-ttu-id="fd55c-111">StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="fd55c-111">StartEnumModules</span></span>](ixclrdataprocess-startenummodules-method.md)                                   | <span data-ttu-id="fd55c-112">提供控制碼來列舉進程的模組。</span><span class="sxs-lookup"><span data-stu-id="fd55c-112">Provides a handle to enumerate the modules of a process.</span></span>                                        |
| [<span data-ttu-id="fd55c-113">EnumModule</span><span class="sxs-lookup"><span data-stu-id="fd55c-113">EnumModule</span></span>](ixclrdataprocess-enummodule-method.md)                                               | <span data-ttu-id="fd55c-114">列舉此進程的模組。</span><span class="sxs-lookup"><span data-stu-id="fd55c-114">Enumerates the modules of this process.</span></span>                                                         |
| [<span data-ttu-id="fd55c-115">EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="fd55c-115">EndEnumModules</span></span>](ixclrdataprocess-endenummodules-method.md)                                       | <span data-ttu-id="fd55c-116">釋放模組列舉期間使用的內部反覆運算器所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="fd55c-116">Releases the resources used by internal iterators used during module enumeration.</span></span>               |
| [<span data-ttu-id="fd55c-117">StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="fd55c-117">StartEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | <span data-ttu-id="fd55c-118">提供控制碼，以列舉 `AppDomain` 從指定位址開始的方法實例。</span><span class="sxs-lookup"><span data-stu-id="fd55c-118">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span> |
| [<span data-ttu-id="fd55c-119">EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="fd55c-119">EnumMethodInstanceByAddress</span></span>](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | <span data-ttu-id="fd55c-120">從位址位移開始，列舉這個進程的方法實例。</span><span class="sxs-lookup"><span data-stu-id="fd55c-120">Enumerates the method instances of this process starting at an address offset.</span></span>                  |
| [<span data-ttu-id="fd55c-121">EndEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="fd55c-121">EndEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | <span data-ttu-id="fd55c-122">釋放實例列舉期間使用的內部反覆運算器所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="fd55c-122">Releases the resources used by internal iterators used during instance enumeration.</span></span>             |

## <a name="remarks"></a><span data-ttu-id="fd55c-123">備註</span><span class="sxs-lookup"><span data-stu-id="fd55c-123">Remarks</span></span>

<span data-ttu-id="fd55c-124">這個介面存在於執行時間內，且不會透過任何標頭或程式庫檔案來公開。</span><span class="sxs-lookup"><span data-stu-id="fd55c-124">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="fd55c-125">不過，它是衍生自的 COM 介面， `IUnknown` `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` 可透過一般的 COM 機制取得 GUID。</span><span class="sxs-lookup"><span data-stu-id="fd55c-125">However, it's a COM interface that derives from `IUnknown` with GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="fd55c-126">規格需求</span><span class="sxs-lookup"><span data-stu-id="fd55c-126">Requirements</span></span>

<span data-ttu-id="fd55c-127">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fd55c-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="fd55c-128">**標頭：** 沒有</span><span class="sxs-lookup"><span data-stu-id="fd55c-128">**Header:** None</span></span>  
<span data-ttu-id="fd55c-129">連結 **庫：** 沒有</span><span class="sxs-lookup"><span data-stu-id="fd55c-129">**Library:** None</span></span>  
<span data-ttu-id="fd55c-130">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fd55c-130">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="fd55c-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd55c-131">See also</span></span>

- [<span data-ttu-id="fd55c-132">偵錯</span><span class="sxs-lookup"><span data-stu-id="fd55c-132">Debugging</span></span>](index.md)
- [<span data-ttu-id="fd55c-133">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="fd55c-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
