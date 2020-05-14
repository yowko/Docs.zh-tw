---
title: IXCLRDataProcess：： EnumMethodInstanceByAddress 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: f3800a5980304394dd648111fe23a3bb0890c575
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395114"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="4b226-102">IXCLRDataProcess：： EnumMethodInstanceByAddress 方法</span><span class="sxs-lookup"><span data-stu-id="4b226-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="4b226-103">從位址位移開始，列舉這個進程的方法實例。</span><span class="sxs-lookup"><span data-stu-id="4b226-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="4b226-104">語法</span><span class="sxs-lookup"><span data-stu-id="4b226-104">Syntax</span></span>

```cpp
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a><span data-ttu-id="4b226-105">參數</span><span class="sxs-lookup"><span data-stu-id="4b226-105">Parameters</span></span>

`handle`\
<span data-ttu-id="4b226-106">在列舉方法實例的控制碼。</span><span class="sxs-lookup"><span data-stu-id="4b226-106">[in] A handle for enumerating the method instances.</span></span>

`mod`\
<span data-ttu-id="4b226-107">脫銷列舉的方法實例。</span><span class="sxs-lookup"><span data-stu-id="4b226-107">[out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="4b226-108">備註</span><span class="sxs-lookup"><span data-stu-id="4b226-108">Remarks</span></span>

<span data-ttu-id="4b226-109">提供的方法是介面的一部分 `IXCLRDataProcess` ，而且會對應至虛擬方法資料表的29個位置。</span><span class="sxs-lookup"><span data-stu-id="4b226-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 29th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="4b226-110">需求</span><span class="sxs-lookup"><span data-stu-id="4b226-110">Requirements</span></span>

<span data-ttu-id="4b226-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4b226-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>
<span data-ttu-id="4b226-112">**標頭：** 無**媒體櫃：** 無 **.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4b226-112">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="4b226-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="4b226-113">See also</span></span>

- [<span data-ttu-id="4b226-114">CLRDataSourceType 列舉</span><span class="sxs-lookup"><span data-stu-id="4b226-114">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="4b226-115">偵錯</span><span class="sxs-lookup"><span data-stu-id="4b226-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="4b226-116">IXCLRDataProcess 介面</span><span class="sxs-lookup"><span data-stu-id="4b226-116">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
