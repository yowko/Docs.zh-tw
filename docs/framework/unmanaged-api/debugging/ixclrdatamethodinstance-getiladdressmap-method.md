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
ms.openlocfilehash: 7c4dcf59ce159434d5012120043f5bb548d49731
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396809"
---
# <a name="ixclrdatamethodinstancegetiladdressmap-method"></a><span data-ttu-id="28fbb-102">IXCLRDataMethodInstance：： GetILAddressMap 方法</span><span class="sxs-lookup"><span data-stu-id="28fbb-102">IXCLRDataMethodInstance::GetILAddressMap Method</span></span>

<span data-ttu-id="28fbb-103">取得用來定址對應資訊的 IL。</span><span class="sxs-lookup"><span data-stu-id="28fbb-103">Gets the IL to address mapping information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="28fbb-104">語法</span><span class="sxs-lookup"><span data-stu-id="28fbb-104">Syntax</span></span>

```cpp
HRESULT GetILAddressMap(
    [in] ULONG32                                   mapLen,
    [out] ULONG32                                 *mapNeeded,
    [out, size_is(mapLen)] CLRDATA_IL_ADDRESS_MAP  maps[]
);
```

## <a name="parameters"></a><span data-ttu-id="28fbb-105">參數</span><span class="sxs-lookup"><span data-stu-id="28fbb-105">Parameters</span></span>

`mapLen`\
<span data-ttu-id="28fbb-106">在所提供對應陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="28fbb-106">[in] The length of the provided maps array.</span></span>

`mapNeeded`\
<span data-ttu-id="28fbb-107">脫銷方法需要的對應專案數目。</span><span class="sxs-lookup"><span data-stu-id="28fbb-107">[out] The number of map entries that the method needs.</span></span>

`maps`\
<span data-ttu-id="28fbb-108">[out，size_is （mapLen）]用於儲存對應專案的陣列。</span><span class="sxs-lookup"><span data-stu-id="28fbb-108">[out, size_is(mapLen)] The array for storing the map entries.</span></span>

## <a name="remarks"></a><span data-ttu-id="28fbb-109">備註</span><span class="sxs-lookup"><span data-stu-id="28fbb-109">Remarks</span></span>

<span data-ttu-id="28fbb-110">提供的方法是介面的一部分 `IXCLRDataMethodInstance` ，而且會對應至虛擬方法資料表的15個插槽。</span><span class="sxs-lookup"><span data-stu-id="28fbb-110">The provided method is part of the `IXCLRDataMethodInstance` interface and corresponds to the 15th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="28fbb-111">需求</span><span class="sxs-lookup"><span data-stu-id="28fbb-111">Requirements</span></span>

<span data-ttu-id="28fbb-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="28fbb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="28fbb-113">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="28fbb-113">**Header:** None</span></span>  
<span data-ttu-id="28fbb-114">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="28fbb-114">**Library:** None</span></span>  
<span data-ttu-id="28fbb-115">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="28fbb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="28fbb-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="28fbb-116">See also</span></span>

- [<span data-ttu-id="28fbb-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="28fbb-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="28fbb-118">IXCLRDataMethodInstance 介面</span><span class="sxs-lookup"><span data-stu-id="28fbb-118">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
