---
title: IXCLRDataMethodDefinition：： EnumInstance 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::EnumInstance Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::EnumInstance Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::EnumInstance Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: b6393d7fa4853c230203521e665bbe89d7b228e2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790435"
---
# <a name="ixclrdatamethoddefinitionenuminstance-method"></a><span data-ttu-id="302df-102">IXCLRDataMethodDefinition：： EnumInstance 方法</span><span class="sxs-lookup"><span data-stu-id="302df-102">IXCLRDataMethodDefinition::EnumInstance Method</span></span>

<span data-ttu-id="302df-103">列舉這個方法定義的實例。</span><span class="sxs-lookup"><span data-stu-id="302df-103">Enumerates the instances of this method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="302df-104">語法</span><span class="sxs-lookup"><span data-stu-id="302df-104">Syntax</span></span>

```cpp
HRESULT EnumInstance(
    [in, out] CLRDATA_ENUM         *handle,
    [out] IXCLRDataMethodInstance **instance
);
```

## <a name="parameters"></a><span data-ttu-id="302df-105">參數</span><span class="sxs-lookup"><span data-stu-id="302df-105">Parameters</span></span>

`handle`\
<span data-ttu-id="302df-106">[in、out]列舉實例的控制碼。</span><span class="sxs-lookup"><span data-stu-id="302df-106">[in, out] A handle for enumerating the instances.</span></span>

`instance`\
<span data-ttu-id="302df-107">脫銷列舉的實例。</span><span class="sxs-lookup"><span data-stu-id="302df-107">[out] The enumerated instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="302df-108">備註</span><span class="sxs-lookup"><span data-stu-id="302df-108">Remarks</span></span>

<span data-ttu-id="302df-109">提供的方法是 `IXCLRDataMethodDefinition` 介面的一部分，而且會對應至虛擬方法資料表的第四個插槽。</span><span class="sxs-lookup"><span data-stu-id="302df-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="302df-110">需求</span><span class="sxs-lookup"><span data-stu-id="302df-110">Requirements</span></span>

<span data-ttu-id="302df-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="302df-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="302df-112">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="302df-112">**Header:** None</span></span>  
<span data-ttu-id="302df-113">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="302df-113">**Library:** None</span></span>  
<span data-ttu-id="302df-114">**.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="302df-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="302df-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="302df-115">See also</span></span>

- [<span data-ttu-id="302df-116">CLRDataSourceType 列舉</span><span class="sxs-lookup"><span data-stu-id="302df-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="302df-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="302df-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="302df-118">IXCLRDataMethodDefinition 介面</span><span class="sxs-lookup"><span data-stu-id="302df-118">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
- [<span data-ttu-id="302df-119">IXCLRDataMethodInstance 介面</span><span class="sxs-lookup"><span data-stu-id="302df-119">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
