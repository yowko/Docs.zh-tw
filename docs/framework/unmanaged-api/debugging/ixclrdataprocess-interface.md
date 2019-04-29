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
ms.openlocfilehash: ff74a7acb5cc84c177f083c19402cd78977aeab5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775241"
---
# <a name="ixclrdataprocess-interface"></a><span data-ttu-id="39071-102">IXCLRDataProcess 介面</span><span class="sxs-lookup"><span data-stu-id="39071-102">IXCLRDataProcess Interface</span></span>

<span data-ttu-id="39071-103">提供方法來查詢處理序的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="39071-103">Provides methods for querying information about a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="39071-104">方法</span><span class="sxs-lookup"><span data-stu-id="39071-104">Methods</span></span>

| <span data-ttu-id="39071-105">方法</span><span class="sxs-lookup"><span data-stu-id="39071-105">Method</span></span>                                                                                                                                               | <span data-ttu-id="39071-106">描述</span><span class="sxs-lookup"><span data-stu-id="39071-106">Description</span></span>                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="39071-107">GetAppDomainByUniqueId</span><span class="sxs-lookup"><span data-stu-id="39071-107">GetAppDomainByUniqueId</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | <span data-ttu-id="39071-108">取得`AppDomain`依其唯一識別碼的處理序中。</span><span class="sxs-lookup"><span data-stu-id="39071-108">Gets an `AppDomain` in a process by its unique id.</span></span>                                              |
| [<span data-ttu-id="39071-109">StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="39071-109">StartEnumModules</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-startenummodules-method.md)                                   | <span data-ttu-id="39071-110">提供列舉的處理程序的模組控制代碼。</span><span class="sxs-lookup"><span data-stu-id="39071-110">Provides a handle to enumerate the modules of a process.</span></span>                                        |
| [<span data-ttu-id="39071-111">EnumModule</span><span class="sxs-lookup"><span data-stu-id="39071-111">EnumModule</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-enummodule-method.md)                                               | <span data-ttu-id="39071-112">列舉此程序的模組。</span><span class="sxs-lookup"><span data-stu-id="39071-112">Enumerates the modules of this process.</span></span>                                                         |
| [<span data-ttu-id="39071-113">EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="39071-113">EndEnumModules</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-endenummodules-method.md)                                       | <span data-ttu-id="39071-114">釋出內部模組列舉期間使用的迭代器所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="39071-114">Releases the resources used by internal iterators used during module enumeration.</span></span>               |
| [<span data-ttu-id="39071-115">StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="39071-115">StartEnumMethodInstancesByAddress</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | <span data-ttu-id="39071-116">提供列舉的方法執行個體的控制代碼`AppDomain`指定位址開頭。</span><span class="sxs-lookup"><span data-stu-id="39071-116">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span> |
| [<span data-ttu-id="39071-117">EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="39071-117">EnumMethodInstanceByAddress</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-enummethodinstancebyaddress-method.md)             | <span data-ttu-id="39071-118">列舉位址位移處開始此程序的方法執行的個體。</span><span class="sxs-lookup"><span data-stu-id="39071-118">Enumerates the method instances of this process starting at an address offset.</span></span>                  |
| [<span data-ttu-id="39071-119">EndEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="39071-119">EndEnumMethodInstancesByAddress</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | <span data-ttu-id="39071-120">釋放執行個體列舉期間使用的內部迭代器所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="39071-120">Releases the resources used by internal iterators used during instance enumeration.</span></span>             |

## <a name="remarks"></a><span data-ttu-id="39071-121">備註</span><span class="sxs-lookup"><span data-stu-id="39071-121">Remarks</span></span>

<span data-ttu-id="39071-122">此介面的執行階段內，而且不會公開透過任何標頭或程式庫檔案。</span><span class="sxs-lookup"><span data-stu-id="39071-122">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="39071-123">不過，它是 COM 介面衍生自`IUnknown`含有 GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` ，可以透過一般的 COM 機制取得。</span><span class="sxs-lookup"><span data-stu-id="39071-123">However, it's a COM interface that derives from `IUnknown` with GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="39071-124">需求</span><span class="sxs-lookup"><span data-stu-id="39071-124">Requirements</span></span>

<span data-ttu-id="39071-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="39071-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="39071-126">**標頭：** None</span><span class="sxs-lookup"><span data-stu-id="39071-126">**Header:** None</span></span>  
<span data-ttu-id="39071-127">**LIBRARY:** None</span><span class="sxs-lookup"><span data-stu-id="39071-127">**Library:** None</span></span>  
<span data-ttu-id="39071-128">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="39071-128">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="39071-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39071-129">See also</span></span>

- [<span data-ttu-id="39071-130">偵錯</span><span class="sxs-lookup"><span data-stu-id="39071-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="39071-131">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="39071-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
