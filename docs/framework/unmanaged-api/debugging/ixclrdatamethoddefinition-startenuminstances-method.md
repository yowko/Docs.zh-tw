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
ms.openlocfilehash: 84e0ad392c5fee8377115427482d80543454fff3
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397199"
---
# <a name="ixclrdatamethoddefinitionstartenuminstances-method"></a><span data-ttu-id="d2d03-102">IXCLRDataMethodDefinition：： StartEnumInstances 方法</span><span class="sxs-lookup"><span data-stu-id="d2d03-102">IXCLRDataMethodDefinition::StartEnumInstances Method</span></span>

<span data-ttu-id="d2d03-103">提供給定的方法實例列舉的控制碼 `IXCLRDataAppDomain` 。</span><span class="sxs-lookup"><span data-stu-id="d2d03-103">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="d2d03-104">語法</span><span class="sxs-lookup"><span data-stu-id="d2d03-104">Syntax</span></span>

```cpp
HRESULT StartEnumInstances(
    [in] IXCLRDataAppDomain* appDomain,
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="d2d03-105">參數</span><span class="sxs-lookup"><span data-stu-id="d2d03-105">Parameters</span></span>

`appDomain`\
<span data-ttu-id="d2d03-106">在列舉的 AppDomain。</span><span class="sxs-lookup"><span data-stu-id="d2d03-106">[in] An AppDomain for the enumeration.</span></span>

`handle`\
<span data-ttu-id="d2d03-107">脫銷列舉實例的控制碼。</span><span class="sxs-lookup"><span data-stu-id="d2d03-107">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="d2d03-108">備註</span><span class="sxs-lookup"><span data-stu-id="d2d03-108">Remarks</span></span>

<span data-ttu-id="d2d03-109">提供的方法是介面的一部分 `IXCLRDataMethodDefinition` ，而且會對應至虛擬方法資料表的第5個位置。</span><span class="sxs-lookup"><span data-stu-id="d2d03-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the 5th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="d2d03-110">需求</span><span class="sxs-lookup"><span data-stu-id="d2d03-110">Requirements</span></span>

<span data-ttu-id="d2d03-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d2d03-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="d2d03-112">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="d2d03-112">**Header:** None</span></span>  
<span data-ttu-id="d2d03-113">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="d2d03-113">**Library:** None</span></span>  
<span data-ttu-id="d2d03-114">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d2d03-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="d2d03-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="d2d03-115">See also</span></span>

- [<span data-ttu-id="d2d03-116">CLRDataSourceType 列舉</span><span class="sxs-lookup"><span data-stu-id="d2d03-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="d2d03-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="d2d03-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="d2d03-118">IXCLRDataMethodDefinition 介面</span><span class="sxs-lookup"><span data-stu-id="d2d03-118">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
