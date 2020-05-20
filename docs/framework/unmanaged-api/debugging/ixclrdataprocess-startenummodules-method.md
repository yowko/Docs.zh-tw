---
title: IXCLRDataProcess：： StartEnumModules 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::StartEnumModules Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::StartEnumModules Method
helpviewer.keywords:
- IXCLRDataProcess::StartEnumModules Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: d55b07ea3fada73237919bf677163a9096d5ad04
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420717"
---
# <a name="ixclrdataprocessstartenummodules-method"></a><span data-ttu-id="ea254-102">IXCLRDataProcess：： StartEnumModules 方法</span><span class="sxs-lookup"><span data-stu-id="ea254-102">IXCLRDataProcess::StartEnumModules Method</span></span>

<span data-ttu-id="ea254-103">提供列舉進程模組的控制碼。</span><span class="sxs-lookup"><span data-stu-id="ea254-103">Provides a handle to enumerate the modules of a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="ea254-104">語法</span><span class="sxs-lookup"><span data-stu-id="ea254-104">Syntax</span></span>

```cpp
HRESULT StartEnumModules(
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="ea254-105">參數</span><span class="sxs-lookup"><span data-stu-id="ea254-105">Parameters</span></span>

`handle`\
<span data-ttu-id="ea254-106">脫銷列舉模組的控制碼。</span><span class="sxs-lookup"><span data-stu-id="ea254-106">[out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="ea254-107">備註</span><span class="sxs-lookup"><span data-stu-id="ea254-107">Remarks</span></span>

<span data-ttu-id="ea254-108">提供的方法是介面的一部分 `IXCLRDataProcess` ，而且會對應至虛擬方法資料表的24日位置。</span><span class="sxs-lookup"><span data-stu-id="ea254-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 24th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="ea254-109">需求</span><span class="sxs-lookup"><span data-stu-id="ea254-109">Requirements</span></span>

<span data-ttu-id="ea254-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ea254-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="ea254-111">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="ea254-111">**Header:** None</span></span>  
<span data-ttu-id="ea254-112">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="ea254-112">**Library:** None</span></span>  
<span data-ttu-id="ea254-113">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ea254-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="ea254-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea254-114">See also</span></span>

- [<span data-ttu-id="ea254-115">CLRDataSourceType 列舉</span><span class="sxs-lookup"><span data-stu-id="ea254-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="ea254-116">偵錯</span><span class="sxs-lookup"><span data-stu-id="ea254-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="ea254-117">IXCLRDataProcess 介面</span><span class="sxs-lookup"><span data-stu-id="ea254-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
