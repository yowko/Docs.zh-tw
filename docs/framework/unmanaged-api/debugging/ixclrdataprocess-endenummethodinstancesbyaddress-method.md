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
ms.openlocfilehash: 04ce8f44b0c9f532951666de7bfb9de475c14746
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395249"
---
# <a name="ixclrdataprocessendenummethodinstancesbyaddress-method"></a><span data-ttu-id="d487b-102">IXCLRDataProcess：： EndEnumMethodInstancesByAddress 方法</span><span class="sxs-lookup"><span data-stu-id="d487b-102">IXCLRDataProcess::EndEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="d487b-103">釋放實例列舉期間所使用之內部反覆運算器所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="d487b-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="d487b-104">語法</span><span class="sxs-lookup"><span data-stu-id="d487b-104">Syntax</span></span>

```cpp
HRESULT EndEnumMethodInstancesByAddress(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="d487b-105">參數</span><span class="sxs-lookup"><span data-stu-id="d487b-105">Parameters</span></span>

`handle`\
<span data-ttu-id="d487b-106">脫銷列舉方法實例的控制碼。</span><span class="sxs-lookup"><span data-stu-id="d487b-106">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="d487b-107">備註</span><span class="sxs-lookup"><span data-stu-id="d487b-107">Remarks</span></span>

<span data-ttu-id="d487b-108">提供的方法是介面的一部分 `IXCLRDataProcess` ，而且會對應至虛擬方法資料表的第30個插槽。</span><span class="sxs-lookup"><span data-stu-id="d487b-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 30th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="d487b-109">需求</span><span class="sxs-lookup"><span data-stu-id="d487b-109">Requirements</span></span>

<span data-ttu-id="d487b-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d487b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="d487b-111">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="d487b-111">**Header:** None</span></span>  
<span data-ttu-id="d487b-112">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="d487b-112">**Library:** None</span></span>  
<span data-ttu-id="d487b-113">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d487b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="d487b-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="d487b-114">See also</span></span>

- [<span data-ttu-id="d487b-115">CLRDataSourceType 列舉</span><span class="sxs-lookup"><span data-stu-id="d487b-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="d487b-116">偵錯</span><span class="sxs-lookup"><span data-stu-id="d487b-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="d487b-117">IXCLRDataProcess 介面</span><span class="sxs-lookup"><span data-stu-id="d487b-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
