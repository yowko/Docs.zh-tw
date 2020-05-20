---
title: ISOSDacInterface：： GetMethodDescData 方法
ms.date: 01/16/2019
api.name:
- ISOSDacInterface::GetMethodDescData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescData Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescData Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 105149d0abf312c33a8498e7428e3a8b23d6ae7d
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421016"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a><span data-ttu-id="a8b3f-102">ISOSDacInterface：： GetMethodDescData 方法</span><span class="sxs-lookup"><span data-stu-id="a8b3f-102">ISOSDacInterface::GetMethodDescData Method</span></span>

<span data-ttu-id="a8b3f-103">取得給定 MethodDesc 指標的資料。</span><span class="sxs-lookup"><span data-stu-id="a8b3f-103">Gets the data for the given MethodDesc pointer.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="a8b3f-104">語法</span><span class="sxs-lookup"><span data-stu-id="a8b3f-104">Syntax</span></span>

```cpp
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    DacpMethodDescData *data,
    ULONG                      cRevertedRejitVersions,
    DacpReJitData      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

## <a name="parameters"></a><span data-ttu-id="a8b3f-105">參數</span><span class="sxs-lookup"><span data-stu-id="a8b3f-105">Parameters</span></span>

`methodDesc`\
<span data-ttu-id="a8b3f-106">在MethodDesc 的位址。</span><span class="sxs-lookup"><span data-stu-id="a8b3f-106">[in] The address of the MethodDesc.</span></span>

`ip`\
<span data-ttu-id="a8b3f-107">在方法的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="a8b3f-107">[in] The IP address of the method.</span></span>

`data`\
<span data-ttu-id="a8b3f-108">脫銷與 MethodDesc 相關聯的資料，如同從內部 Api 傳回的。</span><span class="sxs-lookup"><span data-stu-id="a8b3f-108">[out] The data associated with the MethodDesc as returned from the internal APIs.</span></span>

`cRevertedRejitVersions`\
<span data-ttu-id="a8b3f-109">脫銷已還原的 rejit 版本數目。</span><span class="sxs-lookup"><span data-stu-id="a8b3f-109">[out] The number of reverted rejit versions.</span></span>

`rgRevertedRejitData`\
<span data-ttu-id="a8b3f-110">脫銷與從內部 Api 傳回的還原 rejit 版本相關聯的資料。</span><span class="sxs-lookup"><span data-stu-id="a8b3f-110">[out] The data associated with the reverted rejit versions as returned from the internal APIs.</span></span>

`pcNeededRevertedRejitData`\
<span data-ttu-id="a8b3f-111">脫銷儲存與已還原之 ReJit 版本相關聯之資料所需的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="a8b3f-111">[out] The number of bytes required to store the data associated with the reverted ReJit versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="a8b3f-112">備註</span><span class="sxs-lookup"><span data-stu-id="a8b3f-112">Remarks</span></span>

<span data-ttu-id="a8b3f-113">提供的方法是介面的一部分 `ISOSDacInterface` ，而且會對應至虛擬方法資料表的21個位置。</span><span class="sxs-lookup"><span data-stu-id="a8b3f-113">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 21st slot of the virtual method table.</span></span> <span data-ttu-id="a8b3f-114">若要能夠使用它們， [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) 必須將定義為64位不帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="a8b3f-114">To be able to use them, [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) must be defined as a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="a8b3f-115">需求</span><span class="sxs-lookup"><span data-stu-id="a8b3f-115">Requirements</span></span>

<span data-ttu-id="a8b3f-116">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a8b3f-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="a8b3f-117">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="a8b3f-117">**Header:** None</span></span>  
<span data-ttu-id="a8b3f-118">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="a8b3f-118">**Library:** None</span></span>  
<span data-ttu-id="a8b3f-119">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a8b3f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="a8b3f-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8b3f-120">See also</span></span>

- [<span data-ttu-id="a8b3f-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="a8b3f-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="a8b3f-122">ISOSDacInterface 介面</span><span class="sxs-lookup"><span data-stu-id="a8b3f-122">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
