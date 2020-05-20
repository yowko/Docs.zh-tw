---
title: IXCLRDataProcess：： EnumModule 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumModule Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumModule Method
helpviewer.keywords:
- IXCLRDataProcess::EnumModule Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 5caadcfe091393a8ff79106d57a50a532c349829
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420769"
---
# <a name="ixclrdataprocessenummodule-method"></a><span data-ttu-id="dfefd-102">IXCLRDataProcess：： EnumModule 方法</span><span class="sxs-lookup"><span data-stu-id="dfefd-102">IXCLRDataProcess::EnumModule Method</span></span>

<span data-ttu-id="dfefd-103">列舉此進程的模組。</span><span class="sxs-lookup"><span data-stu-id="dfefd-103">Enumerates the modules of this process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="dfefd-104">語法</span><span class="sxs-lookup"><span data-stu-id="dfefd-104">Syntax</span></span>

```cpp
HRESULT EnumModule(
    [in, out] CLRDATA_ENUM  *handle,
    [out] IXCLRDataModule  **mod
);
```

## <a name="parameters"></a><span data-ttu-id="dfefd-105">參數</span><span class="sxs-lookup"><span data-stu-id="dfefd-105">Parameters</span></span>

`handle`\
<span data-ttu-id="dfefd-106">[in、out]列舉模組的控制碼。</span><span class="sxs-lookup"><span data-stu-id="dfefd-106">[in, out] A handle for enumerating the modules.</span></span>

`mod`\
<span data-ttu-id="dfefd-107">脫銷列舉的模組。</span><span class="sxs-lookup"><span data-stu-id="dfefd-107">[out] The enumerated module.</span></span>

## <a name="remarks"></a><span data-ttu-id="dfefd-108">備註</span><span class="sxs-lookup"><span data-stu-id="dfefd-108">Remarks</span></span>

<span data-ttu-id="dfefd-109">提供的方法是介面的一部分 `IXCLRDataProcess` ，而且會對應至虛擬方法資料表的第25個插槽。</span><span class="sxs-lookup"><span data-stu-id="dfefd-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="dfefd-110">需求</span><span class="sxs-lookup"><span data-stu-id="dfefd-110">Requirements</span></span>

<span data-ttu-id="dfefd-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dfefd-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="dfefd-112">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="dfefd-112">**Header:** None</span></span>  
<span data-ttu-id="dfefd-113">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="dfefd-113">**Library:** None</span></span>  
<span data-ttu-id="dfefd-114">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="dfefd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="dfefd-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfefd-115">See also</span></span>

- [<span data-ttu-id="dfefd-116">CLRDataSourceType 列舉</span><span class="sxs-lookup"><span data-stu-id="dfefd-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="dfefd-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="dfefd-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="dfefd-118">IXCLRDataModule 介面</span><span class="sxs-lookup"><span data-stu-id="dfefd-118">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
- [<span data-ttu-id="dfefd-119">IXCLRDataProcess 介面</span><span class="sxs-lookup"><span data-stu-id="dfefd-119">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
