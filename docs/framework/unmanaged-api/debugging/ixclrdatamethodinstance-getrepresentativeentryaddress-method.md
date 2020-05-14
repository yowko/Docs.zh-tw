---
title: IXCLRDataMethodInstance：： GetRepresentativeEntryAddress 方法
ms.date: 02/01/2019
api.name:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress
helpviewer.keywords:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: d9f9e16d243c0f3b45ac24776caea5bb9c32dcc1
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395743"
---
# <a name="ixclrdatamethodinstancegetrepresentativeentryaddress-method"></a><span data-ttu-id="d7ad8-102">IXCLRDataMethodInstance：： GetRepresentativeEntryAddress 方法</span><span class="sxs-lookup"><span data-stu-id="d7ad8-102">IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method</span></span>

<span data-ttu-id="d7ad8-103">針對方法的所有可能進入點的原生編譯，取得最具代表性的進入點位址。</span><span class="sxs-lookup"><span data-stu-id="d7ad8-103">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="d7ad8-104">語法</span><span class="sxs-lookup"><span data-stu-id="d7ad8-104">Syntax</span></span>

```cpp
HRESULT GetRepresentativeEntryAddress(
    [out] CLRDATA_ADDRESS* addr
);
```

## <a name="parameters"></a><span data-ttu-id="d7ad8-105">參數</span><span class="sxs-lookup"><span data-stu-id="d7ad8-105">Parameters</span></span>

`addr`\
<span data-ttu-id="d7ad8-106">脫銷方法最具代表性的原生進入點位址。</span><span class="sxs-lookup"><span data-stu-id="d7ad8-106">[out] The address of the most representative native entry point for the method.</span></span>

## <a name="remarks"></a><span data-ttu-id="d7ad8-107">備註</span><span class="sxs-lookup"><span data-stu-id="d7ad8-107">Remarks</span></span>

<span data-ttu-id="d7ad8-108">提供的方法是[ `IXCLRDataMethodInstance` 介面](ixclrdatamethodinstance-interface.md)的一部分，而且會對應至虛擬方法資料表的第20個位置。</span><span class="sxs-lookup"><span data-stu-id="d7ad8-108">The provided method is part of the [`IXCLRDataMethodInstance` interface](ixclrdatamethodinstance-interface.md) and corresponds to the 20th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="d7ad8-109">需求</span><span class="sxs-lookup"><span data-stu-id="d7ad8-109">Requirements</span></span>

<span data-ttu-id="d7ad8-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d7ad8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="d7ad8-111">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="d7ad8-111">**Header:** None</span></span>  
<span data-ttu-id="d7ad8-112">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="d7ad8-112">**Library:** None</span></span>  
<span data-ttu-id="d7ad8-113">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d7ad8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="d7ad8-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="d7ad8-114">See also</span></span>

- [<span data-ttu-id="d7ad8-115">偵錯</span><span class="sxs-lookup"><span data-stu-id="d7ad8-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="d7ad8-116">IXCLRDataMethodInstance 介面</span><span class="sxs-lookup"><span data-stu-id="d7ad8-116">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
