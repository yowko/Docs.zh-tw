---
title: IXCLRDataMethodInstance::GetILAddressMap 方法
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
ms.openlocfilehash: 26c86af2c739532c96ce36c36561f8b8f089dd92
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416500"
---
# <a name="ixclrdatamethodinstancegetiladdressmap-method"></a><span data-ttu-id="cb535-102">IXCLRDataMethodInstance::GetILAddressMap 方法</span><span class="sxs-lookup"><span data-stu-id="cb535-102">IXCLRDataMethodInstance::GetILAddressMap Method</span></span>

<span data-ttu-id="cb535-103">取得地址對應資訊的 IL。</span><span class="sxs-lookup"><span data-stu-id="cb535-103">Gets the IL to address mapping information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="cb535-104">語法</span><span class="sxs-lookup"><span data-stu-id="cb535-104">Syntax</span></span>

```
HRESULT GetILAddressMap(
    [in] ULONG32                                   mapLen,
    [out] ULONG32                                 *mapNeeded,
    [out, size_is(mapLen)] CLRDATA_IL_ADDRESS_MAP  maps[]
);
```

### <a name="parameters"></a><span data-ttu-id="cb535-105">參數</span><span class="sxs-lookup"><span data-stu-id="cb535-105">Parameters</span></span>

<span data-ttu-id="cb535-106">`mapLen` [in]提供的對應陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="cb535-106">`mapLen` [in] The length of the provided maps array.</span></span>

<span data-ttu-id="cb535-107">`mapNeeded` [out]此方法需要的對應項目數目。</span><span class="sxs-lookup"><span data-stu-id="cb535-107">`mapNeeded` [out] The number of map entries that the method needs.</span></span>

<span data-ttu-id="cb535-108">`maps` [out，size_is(mapLen)]儲存對應項目的陣列。</span><span class="sxs-lookup"><span data-stu-id="cb535-108">`maps` [out, size_is(mapLen)] The array for storing the map entries.</span></span>

## <a name="remarks"></a><span data-ttu-id="cb535-109">備註</span><span class="sxs-lookup"><span data-stu-id="cb535-109">Remarks</span></span>

<span data-ttu-id="cb535-110">提供的方法是一部分`IXCLRDataMethodInstance`介面，並對應至的虛擬方法表 14 的位置。</span><span class="sxs-lookup"><span data-stu-id="cb535-110">The provided method is part of the `IXCLRDataMethodInstance` interface and corresponds to the 14th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="cb535-111">需求</span><span class="sxs-lookup"><span data-stu-id="cb535-111">Requirements</span></span>

<span data-ttu-id="cb535-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cb535-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="cb535-113">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="cb535-113">**Header:** None</span></span>  
<span data-ttu-id="cb535-114">**程式庫：** 無</span><span class="sxs-lookup"><span data-stu-id="cb535-114">**Library:** None</span></span>  
<span data-ttu-id="cb535-115">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cb535-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="cb535-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb535-116">See Also</span></span>

- [<span data-ttu-id="cb535-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="cb535-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="cb535-118">IXCLRDataMethodInstance 介面</span><span class="sxs-lookup"><span data-stu-id="cb535-118">IXCLRDataMethodInstance Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-interface.md)
