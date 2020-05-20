---
title: IXCLRDataMethodDefinition 介面
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition Interface
helpviewer.keywords:
- IXCLRDataMethodDefinition Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: ebb689eee4a89a70e81d8f9d958e7826c3b3421b
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420951"
---
# <a name="ixclrdatamethoddefinition-interface"></a><span data-ttu-id="684a1-102">IXCLRDataMethodDefinition 介面</span><span class="sxs-lookup"><span data-stu-id="684a1-102">IXCLRDataMethodDefinition Interface</span></span>

<span data-ttu-id="684a1-103">提供查詢方法定義相關資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="684a1-103">Provides methods for querying information about a method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="684a1-104">方法</span><span class="sxs-lookup"><span data-stu-id="684a1-104">Methods</span></span>

<span data-ttu-id="684a1-105">下列方法是介面中可用的一些方法。</span><span class="sxs-lookup"><span data-stu-id="684a1-105">The following methods are some of the methods available in the interface.</span></span>

| <span data-ttu-id="684a1-106">方法</span><span class="sxs-lookup"><span data-stu-id="684a1-106">Method</span></span>                                                                                                                          | <span data-ttu-id="684a1-107">描述</span><span class="sxs-lookup"><span data-stu-id="684a1-107">Description</span></span>                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="684a1-108">StartEnumInstances</span><span class="sxs-lookup"><span data-stu-id="684a1-108">StartEnumInstances</span></span>](ixclrdatamethoddefinition-startenuminstances-method.md) | <span data-ttu-id="684a1-109">提供給定的方法實例列舉的控制碼 `IXCLRDataAppDomain` 。</span><span class="sxs-lookup"><span data-stu-id="684a1-109">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span> |
| [<span data-ttu-id="684a1-110">EnumInstance</span><span class="sxs-lookup"><span data-stu-id="684a1-110">EnumInstance</span></span>](ixclrdatamethoddefinition-enuminstance-method.md)             | <span data-ttu-id="684a1-111">列舉這個方法定義的實例。</span><span class="sxs-lookup"><span data-stu-id="684a1-111">Enumerates the instances of this method definition.</span></span>                                         |
| [<span data-ttu-id="684a1-112">EndEnumInstances</span><span class="sxs-lookup"><span data-stu-id="684a1-112">EndEnumInstances</span></span>](ixclrdatamethoddefinition-endenuminstances-method.md)     | <span data-ttu-id="684a1-113">釋放實例列舉期間所使用之內部反覆運算器所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="684a1-113">Releases the resources used by internal iterators used during instance enumeration.</span></span>         |

## <a name="remarks"></a><span data-ttu-id="684a1-114">備註</span><span class="sxs-lookup"><span data-stu-id="684a1-114">Remarks</span></span>

<span data-ttu-id="684a1-115">這個介面存在於執行時間內，而且不會透過任何標頭或程式庫檔案公開。</span><span class="sxs-lookup"><span data-stu-id="684a1-115">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="684a1-116">不過，它是衍生自的 COM 介面，其 `IUnknown` 具有 `AAF60008-FB2C-420b-8FB1-42D244A54A97` 可透過一般 COM 機制取得的 GUID。</span><span class="sxs-lookup"><span data-stu-id="684a1-116">However, it's a COM interface that derives from `IUnknown` with GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="684a1-117">需求</span><span class="sxs-lookup"><span data-stu-id="684a1-117">Requirements</span></span>

<span data-ttu-id="684a1-118">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="684a1-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="684a1-119">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="684a1-119">**Header:** None</span></span>  
<span data-ttu-id="684a1-120">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="684a1-120">**Library:** None</span></span>  
<span data-ttu-id="684a1-121">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="684a1-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="684a1-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="684a1-122">See also</span></span>

- [<span data-ttu-id="684a1-123">偵錯</span><span class="sxs-lookup"><span data-stu-id="684a1-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="684a1-124">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="684a1-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
