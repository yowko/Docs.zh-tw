---
title: IXCLRDataProcess：： StartEnumMethodInstancesByAddress 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 52d533f1c86b34b7b9febade8590e7ab58d8221e
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420730"
---
# <a name="ixclrdataprocessstartenummethodinstancesbyaddress-method"></a><span data-ttu-id="2c1a4-102">IXCLRDataProcess：： StartEnumMethodInstancesByAddress 方法</span><span class="sxs-lookup"><span data-stu-id="2c1a4-102">IXCLRDataProcess::StartEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="2c1a4-103">提供一個控制碼，用來列舉 `AppDomain` 從指定位址開始的方法實例。</span><span class="sxs-lookup"><span data-stu-id="2c1a4-103">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="2c1a4-104">語法</span><span class="sxs-lookup"><span data-stu-id="2c1a4-104">Syntax</span></span>

```cpp
HRESULT StartEnumMethodInstancesByAddress(
    [in] CLRDATA_ADDRESS     address,
    [in] IXCLRDataAppDomain *appDomain,
    [out] CLRDATA_ENUM      *handle
);
```

## <a name="parameters"></a><span data-ttu-id="2c1a4-105">參數</span><span class="sxs-lookup"><span data-stu-id="2c1a4-105">Parameters</span></span>

`address`\
<span data-ttu-id="2c1a4-106">在第一個方法實例的位址。</span><span class="sxs-lookup"><span data-stu-id="2c1a4-106">[in] The address of the first method instance.</span></span>

`appDomain`\
<span data-ttu-id="2c1a4-107">在方法實例的 AppDomain。</span><span class="sxs-lookup"><span data-stu-id="2c1a4-107">[in] The AppDomain of the method instances.</span></span>

`handle`\
<span data-ttu-id="2c1a4-108">脫銷列舉方法實例的控制碼。</span><span class="sxs-lookup"><span data-stu-id="2c1a4-108">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="2c1a4-109">備註</span><span class="sxs-lookup"><span data-stu-id="2c1a4-109">Remarks</span></span>

<span data-ttu-id="2c1a4-110">提供的方法是介面的一部分 `IXCLRDataProcess` ，而且會對應至虛擬方法資料表的28個位置。</span><span class="sxs-lookup"><span data-stu-id="2c1a4-110">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="2c1a4-111">需求</span><span class="sxs-lookup"><span data-stu-id="2c1a4-111">Requirements</span></span>

<span data-ttu-id="2c1a4-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2c1a4-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="2c1a4-113">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="2c1a4-113">**Header:** None</span></span>  
<span data-ttu-id="2c1a4-114">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="2c1a4-114">**Library:** None</span></span>  
<span data-ttu-id="2c1a4-115">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2c1a4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="2c1a4-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c1a4-116">See also</span></span>

- [<span data-ttu-id="2c1a4-117">CLRDataSourceType 列舉</span><span class="sxs-lookup"><span data-stu-id="2c1a4-117">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="2c1a4-118">偵錯</span><span class="sxs-lookup"><span data-stu-id="2c1a4-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="2c1a4-119">IXCLRDataProcess 介面</span><span class="sxs-lookup"><span data-stu-id="2c1a4-119">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
