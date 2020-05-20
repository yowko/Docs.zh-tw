---
title: IXCLRDataMethodInstance：： GetILAddressMap 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodInstance::GetILAddressMap Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance::GetILAddressMap Method
helpviewer.keywords:
- IXCLRDataMethodInstance::GetILAddressMap Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 0acfa9ffd6f4bc3be567855008dccd08c9c74153
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420912"
---
# <a name="ixclrdatamethodinstancegetiladdressmap-method"></a><span data-ttu-id="f07b7-102">IXCLRDataMethodInstance：： GetILAddressMap 方法</span><span class="sxs-lookup"><span data-stu-id="f07b7-102">IXCLRDataMethodInstance::GetILAddressMap Method</span></span>

<span data-ttu-id="f07b7-103">取得用來定址對應資訊的 IL。</span><span class="sxs-lookup"><span data-stu-id="f07b7-103">Gets the IL to address mapping information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="f07b7-104">語法</span><span class="sxs-lookup"><span data-stu-id="f07b7-104">Syntax</span></span>

```cpp
HRESULT GetILAddressMap(
    [in] ULONG32                                   mapLen,
    [out] ULONG32                                 *mapNeeded,
    [out, size_is(mapLen)] CLRDATA_IL_ADDRESS_MAP  maps[]
);
```

## <a name="parameters"></a><span data-ttu-id="f07b7-105">參數</span><span class="sxs-lookup"><span data-stu-id="f07b7-105">Parameters</span></span>

`mapLen`\
<span data-ttu-id="f07b7-106">在所提供對應陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="f07b7-106">[in] The length of the provided maps array.</span></span>

`mapNeeded`\
<span data-ttu-id="f07b7-107">脫銷方法需要的對應專案數目。</span><span class="sxs-lookup"><span data-stu-id="f07b7-107">[out] The number of map entries that the method needs.</span></span>

`maps`\
<span data-ttu-id="f07b7-108">[out，size_is （mapLen）]用於儲存對應專案的陣列。</span><span class="sxs-lookup"><span data-stu-id="f07b7-108">[out, size_is(mapLen)] The array for storing the map entries.</span></span>

## <a name="remarks"></a><span data-ttu-id="f07b7-109">備註</span><span class="sxs-lookup"><span data-stu-id="f07b7-109">Remarks</span></span>

<span data-ttu-id="f07b7-110">提供的方法是介面的一部分 `IXCLRDataMethodInstance` ，而且會對應至虛擬方法資料表的15個插槽。</span><span class="sxs-lookup"><span data-stu-id="f07b7-110">The provided method is part of the `IXCLRDataMethodInstance` interface and corresponds to the 15th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="f07b7-111">需求</span><span class="sxs-lookup"><span data-stu-id="f07b7-111">Requirements</span></span>

<span data-ttu-id="f07b7-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f07b7-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="f07b7-113">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="f07b7-113">**Header:** None</span></span>  
<span data-ttu-id="f07b7-114">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="f07b7-114">**Library:** None</span></span>  
<span data-ttu-id="f07b7-115">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f07b7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="f07b7-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f07b7-116">See also</span></span>

- [<span data-ttu-id="f07b7-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="f07b7-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="f07b7-118">IXCLRDataMethodInstance 介面</span><span class="sxs-lookup"><span data-stu-id="f07b7-118">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
