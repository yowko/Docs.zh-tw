---
title: IXCLR資料處理：：枚舉方法實例按位址方法
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
ms.openlocfilehash: afc5fc377dd45d5e8d4d2d7b3385ca0524df69e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176652"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="080d4-102">IXCLR資料處理：：枚舉方法實例按位址方法</span><span class="sxs-lookup"><span data-stu-id="080d4-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="080d4-103">枚舉從位址偏移開始此過程的方法實例。</span><span class="sxs-lookup"><span data-stu-id="080d4-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="080d4-104">語法</span><span class="sxs-lookup"><span data-stu-id="080d4-104">Syntax</span></span>

```cpp
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a><span data-ttu-id="080d4-105">參數</span><span class="sxs-lookup"><span data-stu-id="080d4-105">Parameters</span></span>

`handle`\
<span data-ttu-id="080d4-106">[在]用於枚舉方法實例的控制碼。</span><span class="sxs-lookup"><span data-stu-id="080d4-106">[in] A handle for enumerating the method instances.</span></span>

`mod`\
<span data-ttu-id="080d4-107">[出]枚舉的方法實例。</span><span class="sxs-lookup"><span data-stu-id="080d4-107">[out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="080d4-108">備註</span><span class="sxs-lookup"><span data-stu-id="080d4-108">Remarks</span></span>

<span data-ttu-id="080d4-109">提供的方法是介面的一`IXCLRDataProcess`部分，對應于虛擬方法表的第 28 個插槽。</span><span class="sxs-lookup"><span data-stu-id="080d4-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="080d4-110">需求</span><span class="sxs-lookup"><span data-stu-id="080d4-110">Requirements</span></span>

<span data-ttu-id="080d4-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="080d4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>
<span data-ttu-id="080d4-112">**標題：** 無**庫：** 無 **.NET 框架版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="080d4-112">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="080d4-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="080d4-113">See also</span></span>

- [<span data-ttu-id="080d4-114">CLRDataSource 類型枚舉</span><span class="sxs-lookup"><span data-stu-id="080d4-114">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="080d4-115">偵錯</span><span class="sxs-lookup"><span data-stu-id="080d4-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="080d4-116">IXCLRDataProcess 介面</span><span class="sxs-lookup"><span data-stu-id="080d4-116">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
