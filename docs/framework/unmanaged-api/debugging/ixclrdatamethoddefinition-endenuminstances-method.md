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
ms.openlocfilehash: febe6766c7a35228820421eee975c777988efd1f
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396495"
---
# <a name="ixclrdatamethoddefinitionendenuminstances-method"></a><span data-ttu-id="344d8-102">IXCLRDataMethodDefinition：： EndEnumInstances 方法</span><span class="sxs-lookup"><span data-stu-id="344d8-102">IXCLRDataMethodDefinition::EndEnumInstances Method</span></span>

<span data-ttu-id="344d8-103">釋放實例列舉期間所使用之內部反覆運算器所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="344d8-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="344d8-104">語法</span><span class="sxs-lookup"><span data-stu-id="344d8-104">Syntax</span></span>

```cpp
HRESULT EndEnumInstances(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="344d8-105">參數</span><span class="sxs-lookup"><span data-stu-id="344d8-105">Parameters</span></span>

`handle`\
<span data-ttu-id="344d8-106">脫銷列舉實例的控制碼。</span><span class="sxs-lookup"><span data-stu-id="344d8-106">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="344d8-107">備註</span><span class="sxs-lookup"><span data-stu-id="344d8-107">Remarks</span></span>

<span data-ttu-id="344d8-108">提供的方法是介面的一部分 `IXCLRDataMethodDefinition` ，而且會對應至虛擬方法資料表的第7個插槽。</span><span class="sxs-lookup"><span data-stu-id="344d8-108">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the 7th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="344d8-109">需求</span><span class="sxs-lookup"><span data-stu-id="344d8-109">Requirements</span></span>

<span data-ttu-id="344d8-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="344d8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="344d8-111">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="344d8-111">**Header:** None</span></span>  
<span data-ttu-id="344d8-112">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="344d8-112">**Library:** None</span></span>  
<span data-ttu-id="344d8-113">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="344d8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="344d8-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="344d8-114">See also</span></span>

- [<span data-ttu-id="344d8-115">偵錯</span><span class="sxs-lookup"><span data-stu-id="344d8-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="344d8-116">IXCLRDataMethodDefinition 介面</span><span class="sxs-lookup"><span data-stu-id="344d8-116">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
