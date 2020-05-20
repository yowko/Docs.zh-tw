---
title: IXCLRDataProcess：： EndEnumMethodInstancesByAddress 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 5960d08ccfc09010a20d28a22c2e2f3f5b339c7d
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420821"
---
# <a name="ixclrdataprocessendenummethodinstancesbyaddress-method"></a><span data-ttu-id="a90e9-102">IXCLRDataProcess：： EndEnumMethodInstancesByAddress 方法</span><span class="sxs-lookup"><span data-stu-id="a90e9-102">IXCLRDataProcess::EndEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="a90e9-103">釋放實例列舉期間所使用之內部反覆運算器所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="a90e9-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="a90e9-104">語法</span><span class="sxs-lookup"><span data-stu-id="a90e9-104">Syntax</span></span>

```cpp
HRESULT EndEnumMethodInstancesByAddress(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="a90e9-105">參數</span><span class="sxs-lookup"><span data-stu-id="a90e9-105">Parameters</span></span>

`handle`\
<span data-ttu-id="a90e9-106">脫銷列舉方法實例的控制碼。</span><span class="sxs-lookup"><span data-stu-id="a90e9-106">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="a90e9-107">備註</span><span class="sxs-lookup"><span data-stu-id="a90e9-107">Remarks</span></span>

<span data-ttu-id="a90e9-108">提供的方法是介面的一部分 `IXCLRDataProcess` ，而且會對應至虛擬方法資料表的第30個插槽。</span><span class="sxs-lookup"><span data-stu-id="a90e9-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 30th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="a90e9-109">需求</span><span class="sxs-lookup"><span data-stu-id="a90e9-109">Requirements</span></span>

<span data-ttu-id="a90e9-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a90e9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="a90e9-111">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="a90e9-111">**Header:** None</span></span>  
<span data-ttu-id="a90e9-112">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="a90e9-112">**Library:** None</span></span>  
<span data-ttu-id="a90e9-113">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a90e9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="a90e9-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a90e9-114">See also</span></span>

- [<span data-ttu-id="a90e9-115">CLRDataSourceType 列舉</span><span class="sxs-lookup"><span data-stu-id="a90e9-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="a90e9-116">偵錯</span><span class="sxs-lookup"><span data-stu-id="a90e9-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="a90e9-117">IXCLRDataProcess 介面</span><span class="sxs-lookup"><span data-stu-id="a90e9-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
