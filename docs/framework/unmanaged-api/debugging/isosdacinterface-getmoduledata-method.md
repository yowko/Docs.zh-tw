---
title: ISOSDacInterface：： GetModuleData 方法
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetModuleData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetModuleData Method
helpviewer.keywords:
- ISOSDacInterface::GetModuleData Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: b302100eb6cbfa83896cd358762c496ea01f7509
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420977"
---
# <a name="isosdacinterfacegetmoduledata-method"></a><span data-ttu-id="c994d-102">ISOSDacInterface：： GetModuleData 方法</span><span class="sxs-lookup"><span data-stu-id="c994d-102">ISOSDacInterface::GetModuleData Method</span></span>

<span data-ttu-id="c994d-103">提取對應至在指定位址載入之模組的資料。</span><span class="sxs-lookup"><span data-stu-id="c994d-103">Fetches the data corresponding to the module loaded at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="c994d-104">語法</span><span class="sxs-lookup"><span data-stu-id="c994d-104">Syntax</span></span>

```cpp
HRESULT GetModuleData(
    CLRDATA_ADDRESS moduleAddr,
    DacpModuleData *data
);
```

## <a name="parameters"></a><span data-ttu-id="c994d-105">參數</span><span class="sxs-lookup"><span data-stu-id="c994d-105">Parameters</span></span>

`moduleAddr`\
<span data-ttu-id="c994d-106">在要為其取得資訊的模組位址。</span><span class="sxs-lookup"><span data-stu-id="c994d-106">[in] The address of the module to retrieve information for.</span></span>

`data`\
<span data-ttu-id="c994d-107">脫銷用來保存已載入模組之資訊的[dacpmethoddata 結構](dacpmoduledata-structure.md)。</span><span class="sxs-lookup"><span data-stu-id="c994d-107">[out] The [DacpModuleData structure](dacpmoduledata-structure.md) to hold the information of the loaded module.</span></span>

## <a name="remarks"></a><span data-ttu-id="c994d-108">備註</span><span class="sxs-lookup"><span data-stu-id="c994d-108">Remarks</span></span>

<span data-ttu-id="c994d-109">提供的方法是介面的一部分 `ISOSDacInterface` ，而且會對應至虛擬方法資料表的第14個位置。</span><span class="sxs-lookup"><span data-stu-id="c994d-109">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 14th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="c994d-110">需求</span><span class="sxs-lookup"><span data-stu-id="c994d-110">Requirements</span></span>

<span data-ttu-id="c994d-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c994d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="c994d-112">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="c994d-112">**Header:** None</span></span>  
<span data-ttu-id="c994d-113">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="c994d-113">**Library:** None</span></span>  
<span data-ttu-id="c994d-114">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c994d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="c994d-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c994d-115">See also</span></span>

- [<span data-ttu-id="c994d-116">偵錯</span><span class="sxs-lookup"><span data-stu-id="c994d-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="c994d-117">ISOSDacInterface 介面</span><span class="sxs-lookup"><span data-stu-id="c994d-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
