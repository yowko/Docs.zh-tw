---
title: IXCLRDataProcess::EndEnumModules 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumModules Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumModules Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumModules Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 3b7050e92af6fc58b45837840b2796a5deac955c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375333"
---
# <a name="ixclrdataprocessendenummodules-method"></a><span data-ttu-id="44da0-102">IXCLRDataProcess::EndEnumModules 方法</span><span class="sxs-lookup"><span data-stu-id="44da0-102">IXCLRDataProcess::EndEnumModules Method</span></span>

<span data-ttu-id="44da0-103">釋出內部模組列舉期間使用的迭代器所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="44da0-103">Releases the resources used by internal iterators used during module enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="44da0-104">語法</span><span class="sxs-lookup"><span data-stu-id="44da0-104">Syntax</span></span>
```
HRESULT EndEnumModules(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="44da0-105">參數</span><span class="sxs-lookup"><span data-stu-id="44da0-105">Parameters</span></span>

`handle`\
<span data-ttu-id="44da0-106">[out]列舉模組控制代碼。</span><span class="sxs-lookup"><span data-stu-id="44da0-106">[out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="44da0-107">備註</span><span class="sxs-lookup"><span data-stu-id="44da0-107">Remarks</span></span>

<span data-ttu-id="44da0-108">提供的方法是一部分`IXCLRDataProcess`介面，並對應至的虛擬方法表 26 的位置。</span><span class="sxs-lookup"><span data-stu-id="44da0-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 26th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="44da0-109">需求</span><span class="sxs-lookup"><span data-stu-id="44da0-109">Requirements</span></span>

<span data-ttu-id="44da0-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="44da0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="44da0-111">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="44da0-111">**Header:** None</span></span>   
<span data-ttu-id="44da0-112">**程式庫：** 無</span><span class="sxs-lookup"><span data-stu-id="44da0-112">**Library:** None</span></span>   
<span data-ttu-id="44da0-113">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="44da0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>   

## <a name="see-also"></a><span data-ttu-id="44da0-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44da0-114">See also</span></span>

- [<span data-ttu-id="44da0-115">偵錯</span><span class="sxs-lookup"><span data-stu-id="44da0-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="44da0-116">IXCLRDataProcess 介面</span><span class="sxs-lookup"><span data-stu-id="44da0-116">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
