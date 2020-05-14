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
ms.openlocfilehash: ff8ccf42d1131fb15d7473ae12ecefde9d55177f
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395283"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="19608-102">IXCLRDataModule：： GetVersionId 方法</span><span class="sxs-lookup"><span data-stu-id="19608-102">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="19608-103">取得模組的版本識別碼。</span><span class="sxs-lookup"><span data-stu-id="19608-103">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="19608-104">語法</span><span class="sxs-lookup"><span data-stu-id="19608-104">Syntax</span></span>

```cpp
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a><span data-ttu-id="19608-105">參數</span><span class="sxs-lookup"><span data-stu-id="19608-105">Parameters</span></span>

`vid`\
<span data-ttu-id="19608-106">脫銷模組的版本識別碼。</span><span class="sxs-lookup"><span data-stu-id="19608-106">[out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="19608-107">備註</span><span class="sxs-lookup"><span data-stu-id="19608-107">Remarks</span></span>

<span data-ttu-id="19608-108">提供的方法是介面的一部分 `IXCLRDataModule` ，而且會對應至虛擬方法資料表的 schema-agnostic indexing with 位置。</span><span class="sxs-lookup"><span data-stu-id="19608-108">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 41st slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="19608-109">需求</span><span class="sxs-lookup"><span data-stu-id="19608-109">Requirements</span></span>

<span data-ttu-id="19608-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="19608-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="19608-111">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="19608-111">**Header:** None</span></span>  
<span data-ttu-id="19608-112">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="19608-112">**Library:** None</span></span>  
<span data-ttu-id="19608-113">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="19608-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="19608-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="19608-114">See also</span></span>

- [<span data-ttu-id="19608-115">偵錯</span><span class="sxs-lookup"><span data-stu-id="19608-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="19608-116">IXCLRDataModule 介面</span><span class="sxs-lookup"><span data-stu-id="19608-116">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
