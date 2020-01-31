---
title: IXCLRDataMethodDefinition：： EndEnumInstances 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::EndEnumInstances Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::EndEnumInstances Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::EndEnumInstances Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 605a4244d20ef6c0b7af3c2b26b65ff2a63fa9dd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790451"
---
# <a name="ixclrdatamethoddefinitionendenuminstances-method"></a><span data-ttu-id="e0ff6-102">IXCLRDataMethodDefinition：： EndEnumInstances 方法</span><span class="sxs-lookup"><span data-stu-id="e0ff6-102">IXCLRDataMethodDefinition::EndEnumInstances Method</span></span>

<span data-ttu-id="e0ff6-103">釋放實例列舉期間所使用之內部反覆運算器所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="e0ff6-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="e0ff6-104">語法</span><span class="sxs-lookup"><span data-stu-id="e0ff6-104">Syntax</span></span>

```cpp
HRESULT EndEnumInstances(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="e0ff6-105">參數</span><span class="sxs-lookup"><span data-stu-id="e0ff6-105">Parameters</span></span>

`handle`\
<span data-ttu-id="e0ff6-106">脫銷列舉實例的控制碼。</span><span class="sxs-lookup"><span data-stu-id="e0ff6-106">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="e0ff6-107">備註</span><span class="sxs-lookup"><span data-stu-id="e0ff6-107">Remarks</span></span>

<span data-ttu-id="e0ff6-108">提供的方法是 `IXCLRDataMethodDefinition` 介面的一部分，而且會對應至虛擬方法資料表的第五個插槽。</span><span class="sxs-lookup"><span data-stu-id="e0ff6-108">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fifth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="e0ff6-109">需求</span><span class="sxs-lookup"><span data-stu-id="e0ff6-109">Requirements</span></span>

<span data-ttu-id="e0ff6-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e0ff6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="e0ff6-111">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="e0ff6-111">**Header:** None</span></span>  
<span data-ttu-id="e0ff6-112">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="e0ff6-112">**Library:** None</span></span>  
<span data-ttu-id="e0ff6-113">**.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e0ff6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="e0ff6-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="e0ff6-114">See also</span></span>

- [<span data-ttu-id="e0ff6-115">偵錯</span><span class="sxs-lookup"><span data-stu-id="e0ff6-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="e0ff6-116">IXCLRDataMethodDefinition 介面</span><span class="sxs-lookup"><span data-stu-id="e0ff6-116">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
