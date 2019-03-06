---
title: IXCLRDataProcess::EndEnumMethodInstancesByAddress 方法
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
ms.openlocfilehash: 072e775d11d44dfbca27f1616889e388ae61d467
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365993"
---
# <a name="ixclrdataprocessendenummethodinstancesbyaddress-method"></a><span data-ttu-id="6a69c-102">IXCLRDataProcess::EndEnumMethodInstancesByAddress 方法</span><span class="sxs-lookup"><span data-stu-id="6a69c-102">IXCLRDataProcess::EndEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="6a69c-103">釋放執行個體列舉期間使用的內部迭代器所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="6a69c-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="6a69c-104">語法</span><span class="sxs-lookup"><span data-stu-id="6a69c-104">Syntax</span></span>

```
HRESULT EndEnumMethodInstancesByAddress(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="6a69c-105">參數</span><span class="sxs-lookup"><span data-stu-id="6a69c-105">Parameters</span></span>

`handle`\
<span data-ttu-id="6a69c-106">[out]列舉的方法執行個體控制代碼。</span><span class="sxs-lookup"><span data-stu-id="6a69c-106">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="6a69c-107">備註</span><span class="sxs-lookup"><span data-stu-id="6a69c-107">Remarks</span></span>

<span data-ttu-id="6a69c-108">提供的方法是一部分`IXCLRDataProcess`介面，並對應到第 29 虛擬方法表的位置。</span><span class="sxs-lookup"><span data-stu-id="6a69c-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 29th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="6a69c-109">需求</span><span class="sxs-lookup"><span data-stu-id="6a69c-109">Requirements</span></span>

<span data-ttu-id="6a69c-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6a69c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="6a69c-111">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="6a69c-111">**Header:** None</span></span>  
<span data-ttu-id="6a69c-112">**程式庫：** 無</span><span class="sxs-lookup"><span data-stu-id="6a69c-112">**Library:** None</span></span>  
<span data-ttu-id="6a69c-113">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6a69c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="6a69c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a69c-114">See also</span></span>

- [<span data-ttu-id="6a69c-115">CLRDataSourceType 列舉</span><span class="sxs-lookup"><span data-stu-id="6a69c-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="6a69c-116">偵錯</span><span class="sxs-lookup"><span data-stu-id="6a69c-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="6a69c-117">IXCLRDataProcess 介面</span><span class="sxs-lookup"><span data-stu-id="6a69c-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
