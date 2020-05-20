---
title: IXCLRDataModule：： GetMethodDefinitionByToken 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::GetMethodDefinitionByToken Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::GetMethodDefinitionByToken Method
helpviewer.keywords:
- IXCLRDataModule::GetMethodDefinitionByToken Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 074949145be588fc34266a9f2ee501caeeffb9d3
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420873"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a><span data-ttu-id="05d3d-102">IXCLRDataModule：： GetMethodDefinitionByToken 方法</span><span class="sxs-lookup"><span data-stu-id="05d3d-102">IXCLRDataModule::GetMethodDefinitionByToken Method</span></span>

<span data-ttu-id="05d3d-103">取得對應至指定之元資料標記的方法定義。</span><span class="sxs-lookup"><span data-stu-id="05d3d-103">Gets the method definition corresponding to a given metadata token.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="05d3d-104">語法</span><span class="sxs-lookup"><span data-stu-id="05d3d-104">Syntax</span></span>

```cpp
HRESULT GetMethodDefinitionByToken(
    [in] mdMethodDef token,
    [out] IXCLRDataMethodDefinition** methodDefinition
);
```

## <a name="parameters"></a><span data-ttu-id="05d3d-105">參數</span><span class="sxs-lookup"><span data-stu-id="05d3d-105">Parameters</span></span>

`token`\
<span data-ttu-id="05d3d-106">在方法 token。</span><span class="sxs-lookup"><span data-stu-id="05d3d-106">[in] The method token.</span></span>

`methodDefinition`\
<span data-ttu-id="05d3d-107">脫銷方法定義。</span><span class="sxs-lookup"><span data-stu-id="05d3d-107">[out] The method definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="05d3d-108">備註</span><span class="sxs-lookup"><span data-stu-id="05d3d-108">Remarks</span></span>

<span data-ttu-id="05d3d-109">提供的方法是介面的一部分 `IXCLRDataModule` ，而且會對應至虛擬方法資料表的26個位置。</span><span class="sxs-lookup"><span data-stu-id="05d3d-109">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 26th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="05d3d-110">需求</span><span class="sxs-lookup"><span data-stu-id="05d3d-110">Requirements</span></span>

<span data-ttu-id="05d3d-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="05d3d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="05d3d-112">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="05d3d-112">**Header:** None</span></span>  
<span data-ttu-id="05d3d-113">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="05d3d-113">**Library:** None</span></span>  
<span data-ttu-id="05d3d-114">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="05d3d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="05d3d-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05d3d-115">See also</span></span>

- [<span data-ttu-id="05d3d-116">偵錯</span><span class="sxs-lookup"><span data-stu-id="05d3d-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="05d3d-117">IXCLRDataModule 介面</span><span class="sxs-lookup"><span data-stu-id="05d3d-117">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
