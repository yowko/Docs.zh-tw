---
title: IXCLRDataMethodDefinition：： StartEnumInstances 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::StartEnumInstances Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::StartEnumInstances Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::StartEnumInstances Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: b0c37c666f23f04239ed827246b87c43ee8d5ad9
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420925"
---
# <a name="ixclrdatamethoddefinitionstartenuminstances-method"></a><span data-ttu-id="2c70a-102">IXCLRDataMethodDefinition：： StartEnumInstances 方法</span><span class="sxs-lookup"><span data-stu-id="2c70a-102">IXCLRDataMethodDefinition::StartEnumInstances Method</span></span>

<span data-ttu-id="2c70a-103">提供給定的方法實例列舉的控制碼 `IXCLRDataAppDomain` 。</span><span class="sxs-lookup"><span data-stu-id="2c70a-103">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="2c70a-104">語法</span><span class="sxs-lookup"><span data-stu-id="2c70a-104">Syntax</span></span>

```cpp
HRESULT StartEnumInstances(
    [in] IXCLRDataAppDomain* appDomain,
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="2c70a-105">參數</span><span class="sxs-lookup"><span data-stu-id="2c70a-105">Parameters</span></span>

`appDomain`\
<span data-ttu-id="2c70a-106">在列舉的 AppDomain。</span><span class="sxs-lookup"><span data-stu-id="2c70a-106">[in] An AppDomain for the enumeration.</span></span>

`handle`\
<span data-ttu-id="2c70a-107">脫銷列舉實例的控制碼。</span><span class="sxs-lookup"><span data-stu-id="2c70a-107">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="2c70a-108">備註</span><span class="sxs-lookup"><span data-stu-id="2c70a-108">Remarks</span></span>

<span data-ttu-id="2c70a-109">提供的方法是介面的一部分 `IXCLRDataMethodDefinition` ，而且會對應至虛擬方法資料表的第5個位置。</span><span class="sxs-lookup"><span data-stu-id="2c70a-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the 5th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="2c70a-110">需求</span><span class="sxs-lookup"><span data-stu-id="2c70a-110">Requirements</span></span>

<span data-ttu-id="2c70a-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2c70a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="2c70a-112">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="2c70a-112">**Header:** None</span></span>  
<span data-ttu-id="2c70a-113">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="2c70a-113">**Library:** None</span></span>  
<span data-ttu-id="2c70a-114">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2c70a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="2c70a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c70a-115">See also</span></span>

- [<span data-ttu-id="2c70a-116">CLRDataSourceType 列舉</span><span class="sxs-lookup"><span data-stu-id="2c70a-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="2c70a-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="2c70a-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="2c70a-118">IXCLRDataMethodDefinition 介面</span><span class="sxs-lookup"><span data-stu-id="2c70a-118">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
