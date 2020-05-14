---
title: ISOSDacInterface：： GetMethodDescPtrFromIP 方法
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 0c8d91c11205e06857b4a6e7edfedcd087270d00
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396933"
---
# <a name="isosdacinterfacegetmethoddescptrfromip-method"></a><span data-ttu-id="30bb3-102">ISOSDacInterface：： GetMethodDescPtrFromIP 方法</span><span class="sxs-lookup"><span data-stu-id="30bb3-102">ISOSDacInterface::GetMethodDescPtrFromIP Method</span></span>

<span data-ttu-id="30bb3-103">抓取 MethodDesc 的指標，其對應的方法包含指定的原生指令位址。</span><span class="sxs-lookup"><span data-stu-id="30bb3-103">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="30bb3-104">語法</span><span class="sxs-lookup"><span data-stu-id="30bb3-104">Syntax</span></span>

```cpp
HRESULT GetMethodDescPtrFromIP(
    CLRDATA_ADDRESS ip,
    CLRDATA_ADDRESS * ppMD
);
```

## <a name="parameters"></a><span data-ttu-id="30bb3-105">參數</span><span class="sxs-lookup"><span data-stu-id="30bb3-105">Parameters</span></span>

`ip`\
<span data-ttu-id="30bb3-106">在在執行時間的方法內的位址。</span><span class="sxs-lookup"><span data-stu-id="30bb3-106">[in] An address within the method at runtime.</span></span>

`ppMD`\
<span data-ttu-id="30bb3-107">脫銷特定方法的位址 `MethodDesc` 。</span><span class="sxs-lookup"><span data-stu-id="30bb3-107">[out] The address of the `MethodDesc` for the particular method.</span></span>

## <a name="remarks"></a><span data-ttu-id="30bb3-108">備註</span><span class="sxs-lookup"><span data-stu-id="30bb3-108">Remarks</span></span>

<span data-ttu-id="30bb3-109">提供的方法是[ `ISOSDacInterface` 介面](isosdacinterface-interface.md)的一部分，而且會對應至虛擬方法資料表的22日位置。</span><span class="sxs-lookup"><span data-stu-id="30bb3-109">The provided method is part of the [`ISOSDacInterface` interface](isosdacinterface-interface.md) and corresponds to the 22nd slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="30bb3-110">需求</span><span class="sxs-lookup"><span data-stu-id="30bb3-110">Requirements</span></span>

<span data-ttu-id="30bb3-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="30bb3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="30bb3-112">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="30bb3-112">**Header:** None</span></span>  
<span data-ttu-id="30bb3-113">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="30bb3-113">**Library:** None</span></span>  
<span data-ttu-id="30bb3-114">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="30bb3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="30bb3-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="30bb3-115">See also</span></span>

- [<span data-ttu-id="30bb3-116">偵錯</span><span class="sxs-lookup"><span data-stu-id="30bb3-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="30bb3-117">ISOSDacInterface 介面</span><span class="sxs-lookup"><span data-stu-id="30bb3-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
