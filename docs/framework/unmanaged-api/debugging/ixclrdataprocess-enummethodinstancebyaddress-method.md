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
ms.openlocfilehash: 142099ae5cf9637cc28e8c82aabcd831cc8f0f52
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420795"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="62af8-102">IXCLRDataProcess：： EnumMethodInstanceByAddress 方法</span><span class="sxs-lookup"><span data-stu-id="62af8-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="62af8-103">從位址位移開始，列舉這個進程的方法實例。</span><span class="sxs-lookup"><span data-stu-id="62af8-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="62af8-104">語法</span><span class="sxs-lookup"><span data-stu-id="62af8-104">Syntax</span></span>

```cpp
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a><span data-ttu-id="62af8-105">參數</span><span class="sxs-lookup"><span data-stu-id="62af8-105">Parameters</span></span>

`handle`\
<span data-ttu-id="62af8-106">在列舉方法實例的控制碼。</span><span class="sxs-lookup"><span data-stu-id="62af8-106">[in] A handle for enumerating the method instances.</span></span>

`mod`\
<span data-ttu-id="62af8-107">脫銷列舉的方法實例。</span><span class="sxs-lookup"><span data-stu-id="62af8-107">[out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="62af8-108">備註</span><span class="sxs-lookup"><span data-stu-id="62af8-108">Remarks</span></span>

<span data-ttu-id="62af8-109">提供的方法是介面的一部分 `IXCLRDataProcess` ，而且會對應至虛擬方法資料表的29個位置。</span><span class="sxs-lookup"><span data-stu-id="62af8-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 29th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="62af8-110">需求</span><span class="sxs-lookup"><span data-stu-id="62af8-110">Requirements</span></span>

<span data-ttu-id="62af8-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="62af8-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="62af8-112">**標頭：** 無**媒體櫃：** 無 **.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="62af8-112">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="62af8-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62af8-113">See also</span></span>

- [<span data-ttu-id="62af8-114">CLRDataSourceType 列舉</span><span class="sxs-lookup"><span data-stu-id="62af8-114">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="62af8-115">偵錯</span><span class="sxs-lookup"><span data-stu-id="62af8-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="62af8-116">IXCLRDataProcess 介面</span><span class="sxs-lookup"><span data-stu-id="62af8-116">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
