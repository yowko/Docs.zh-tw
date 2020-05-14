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
ms.openlocfilehash: 72560de9777b2d826418e63b4a4fcccf1e4fa8b9
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396474"
---
# <a name="ixclrdatamethoddefinitionenuminstance-method"></a><span data-ttu-id="b4443-102">IXCLRDataMethodDefinition：： EnumInstance 方法</span><span class="sxs-lookup"><span data-stu-id="b4443-102">IXCLRDataMethodDefinition::EnumInstance Method</span></span>

<span data-ttu-id="b4443-103">列舉這個方法定義的實例。</span><span class="sxs-lookup"><span data-stu-id="b4443-103">Enumerates the instances of this method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="b4443-104">語法</span><span class="sxs-lookup"><span data-stu-id="b4443-104">Syntax</span></span>

```cpp
HRESULT EnumInstance(
    [in, out] CLRDATA_ENUM         *handle,
    [out] IXCLRDataMethodInstance **instance
);
```

## <a name="parameters"></a><span data-ttu-id="b4443-105">參數</span><span class="sxs-lookup"><span data-stu-id="b4443-105">Parameters</span></span>

`handle`\
<span data-ttu-id="b4443-106">[in、out]列舉實例的控制碼。</span><span class="sxs-lookup"><span data-stu-id="b4443-106">[in, out] A handle for enumerating the instances.</span></span>

`instance`\
<span data-ttu-id="b4443-107">脫銷列舉的實例。</span><span class="sxs-lookup"><span data-stu-id="b4443-107">[out] The enumerated instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="b4443-108">備註</span><span class="sxs-lookup"><span data-stu-id="b4443-108">Remarks</span></span>

<span data-ttu-id="b4443-109">提供的方法是介面的一部分 `IXCLRDataMethodDefinition` ，而且會對應至虛擬方法資料表的第6個插槽。</span><span class="sxs-lookup"><span data-stu-id="b4443-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the 6th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="b4443-110">需求</span><span class="sxs-lookup"><span data-stu-id="b4443-110">Requirements</span></span>

<span data-ttu-id="b4443-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b4443-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="b4443-112">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="b4443-112">**Header:** None</span></span>  
<span data-ttu-id="b4443-113">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="b4443-113">**Library:** None</span></span>  
<span data-ttu-id="b4443-114">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b4443-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="b4443-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="b4443-115">See also</span></span>

- [<span data-ttu-id="b4443-116">CLRDataSourceType 列舉</span><span class="sxs-lookup"><span data-stu-id="b4443-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="b4443-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="b4443-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="b4443-118">IXCLRDataMethodDefinition 介面</span><span class="sxs-lookup"><span data-stu-id="b4443-118">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
- [<span data-ttu-id="b4443-119">IXCLRDataMethodInstance 介面</span><span class="sxs-lookup"><span data-stu-id="b4443-119">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
