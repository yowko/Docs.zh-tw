---
title: IXCLRDataModule：： GetVersionId 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::GetVersionId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::GetVersionId Method
helpviewer.keywords:
- IXCLRDataModule::GetVersionId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 9d5ef137a5d76c3d7545ab16921352123e978fb1
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420860"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="da1d4-102">IXCLRDataModule：： GetVersionId 方法</span><span class="sxs-lookup"><span data-stu-id="da1d4-102">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="da1d4-103">取得模組的版本識別碼。</span><span class="sxs-lookup"><span data-stu-id="da1d4-103">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="da1d4-104">語法</span><span class="sxs-lookup"><span data-stu-id="da1d4-104">Syntax</span></span>

```cpp
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a><span data-ttu-id="da1d4-105">參數</span><span class="sxs-lookup"><span data-stu-id="da1d4-105">Parameters</span></span>

`vid`\
<span data-ttu-id="da1d4-106">脫銷模組的版本識別碼。</span><span class="sxs-lookup"><span data-stu-id="da1d4-106">[out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="da1d4-107">備註</span><span class="sxs-lookup"><span data-stu-id="da1d4-107">Remarks</span></span>

<span data-ttu-id="da1d4-108">提供的方法是介面的一部分 `IXCLRDataModule` ，而且會對應至虛擬方法資料表的 schema-agnostic indexing with 位置。</span><span class="sxs-lookup"><span data-stu-id="da1d4-108">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 41st slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="da1d4-109">需求</span><span class="sxs-lookup"><span data-stu-id="da1d4-109">Requirements</span></span>

<span data-ttu-id="da1d4-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="da1d4-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="da1d4-111">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="da1d4-111">**Header:** None</span></span>  
<span data-ttu-id="da1d4-112">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="da1d4-112">**Library:** None</span></span>  
<span data-ttu-id="da1d4-113">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="da1d4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="da1d4-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da1d4-114">See also</span></span>

- [<span data-ttu-id="da1d4-115">偵錯</span><span class="sxs-lookup"><span data-stu-id="da1d4-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="da1d4-116">IXCLRDataModule 介面</span><span class="sxs-lookup"><span data-stu-id="da1d4-116">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
