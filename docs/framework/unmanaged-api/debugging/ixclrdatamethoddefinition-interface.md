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
ms.openlocfilehash: 4b1e8cb1cf34bb1c5ade1353351aab953e2b734a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54644243"
---
# <a name="ixclrdatamethoddefinition-interface"></a><span data-ttu-id="c30bd-102">IXCLRDataMethodDefinition 介面</span><span class="sxs-lookup"><span data-stu-id="c30bd-102">IXCLRDataMethodDefinition Interface</span></span>

<span data-ttu-id="c30bd-103">提供方法來查詢方法定義的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c30bd-103">Provides methods for querying information about a method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="c30bd-104">方法</span><span class="sxs-lookup"><span data-stu-id="c30bd-104">Methods</span></span>

<span data-ttu-id="c30bd-105">下列方法是一些在介面中可用的方法。</span><span class="sxs-lookup"><span data-stu-id="c30bd-105">The following methods are some of the methods available in the interface.</span></span>

| <span data-ttu-id="c30bd-106">方法</span><span class="sxs-lookup"><span data-stu-id="c30bd-106">Method</span></span>                                                                                                                          | <span data-ttu-id="c30bd-107">描述</span><span class="sxs-lookup"><span data-stu-id="c30bd-107">Description</span></span>                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="c30bd-108">StartEnumInstances</span><span class="sxs-lookup"><span data-stu-id="c30bd-108">StartEnumInstances</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-startenuminstances-method.md) | <span data-ttu-id="c30bd-109">提供的控制代碼的方法執行個體的列舉型別的指定`IXCLRDataAppDomain`。</span><span class="sxs-lookup"><span data-stu-id="c30bd-109">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span> |
| [<span data-ttu-id="c30bd-110">EnumInstance</span><span class="sxs-lookup"><span data-stu-id="c30bd-110">EnumInstance</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-enuminstance-method.md)             | <span data-ttu-id="c30bd-111">列舉的執行個體，這個方法定義。</span><span class="sxs-lookup"><span data-stu-id="c30bd-111">Enumerates the instances of this method definition.</span></span>                                         |
| [<span data-ttu-id="c30bd-112">EndEnumInstances</span><span class="sxs-lookup"><span data-stu-id="c30bd-112">EndEnumInstances</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-endenuminstances-method.md)     | <span data-ttu-id="c30bd-113">釋放執行個體列舉期間使用的內部迭代器所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="c30bd-113">Releases the resources used by internal iterators used during instance enumeration.</span></span>         |

## <a name="remarks"></a><span data-ttu-id="c30bd-114">備註</span><span class="sxs-lookup"><span data-stu-id="c30bd-114">Remarks</span></span>

<span data-ttu-id="c30bd-115">此介面的執行階段內，而且不會公開透過任何標頭或程式庫檔案。</span><span class="sxs-lookup"><span data-stu-id="c30bd-115">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="c30bd-116">不過，它是 COM 介面衍生自`IUnknown`含有 GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97` ，可以透過一般的 COM 機制取得。</span><span class="sxs-lookup"><span data-stu-id="c30bd-116">However, it's a COM interface that derives from `IUnknown` with GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="c30bd-117">需求</span><span class="sxs-lookup"><span data-stu-id="c30bd-117">Requirements</span></span>

<span data-ttu-id="c30bd-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c30bd-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="c30bd-119">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="c30bd-119">**Header:** None</span></span>  
<span data-ttu-id="c30bd-120">**程式庫：** 無</span><span class="sxs-lookup"><span data-stu-id="c30bd-120">**Library:** None</span></span>  
<span data-ttu-id="c30bd-121">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c30bd-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="c30bd-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c30bd-122">See also</span></span>

- [<span data-ttu-id="c30bd-123">偵錯</span><span class="sxs-lookup"><span data-stu-id="c30bd-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="c30bd-124">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="c30bd-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
