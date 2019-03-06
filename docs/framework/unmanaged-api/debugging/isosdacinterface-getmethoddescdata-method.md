---
title: ISOSDacInterface::GetMethodDescData 方法
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
ms.openlocfilehash: 4e32facc65162c4deb853cd507a00126e5f786e7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352590"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a><span data-ttu-id="d8546-102">ISOSDacInterface::GetMethodDescData 方法</span><span class="sxs-lookup"><span data-stu-id="d8546-102">ISOSDacInterface::GetMethodDescData Method</span></span>

<span data-ttu-id="d8546-103">取得指定 MethodDesc 指標的資料。</span><span class="sxs-lookup"><span data-stu-id="d8546-103">Gets the data for the given MethodDesc pointer.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="d8546-104">語法</span><span class="sxs-lookup"><span data-stu-id="d8546-104">Syntax</span></span>

```
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    DacpMethodDescData *data,
    ULONG                      cRevertedRejitVersions,
    DacpReJitData      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

## <a name="parameters"></a><span data-ttu-id="d8546-105">參數</span><span class="sxs-lookup"><span data-stu-id="d8546-105">Parameters</span></span>

`methodDesc`\
<span data-ttu-id="d8546-106">[in]MethodDesc 位址。</span><span class="sxs-lookup"><span data-stu-id="d8546-106">[in] The address of the MethodDesc.</span></span>

`ip`\
<span data-ttu-id="d8546-107">[in]方法的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="d8546-107">[in] The IP address of the method.</span></span>

`data`\
<span data-ttu-id="d8546-108">[out]傳回從內部 Api，與 MethodDesc 相關的資料。</span><span class="sxs-lookup"><span data-stu-id="d8546-108">[out] The data associated with the MethodDesc as returned from the internal APIs.</span></span>

`cRevertedRejitVersions`\
<span data-ttu-id="d8546-109">[out]已還原的 rejit 版本數目。</span><span class="sxs-lookup"><span data-stu-id="d8546-109">[out] The number of reverted rejit versions.</span></span>

`rgRevertedRejitData`\
<span data-ttu-id="d8546-110">[out]傳回的內部 Api，以還原的 rejit 版本相關聯的資料。</span><span class="sxs-lookup"><span data-stu-id="d8546-110">[out] The data associated with the reverted rejit versions as returned from the internal APIs.</span></span>

`pcNeededRevertedRejitData`\
<span data-ttu-id="d8546-111">[out]儲存與還原的 ReJit 版本相關聯的資料所需的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="d8546-111">[out] The number of bytes required to store the data associated with the reverted ReJit versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="d8546-112">備註</span><span class="sxs-lookup"><span data-stu-id="d8546-112">Remarks</span></span>

<span data-ttu-id="d8546-113">提供的方法是一部分`ISOSDacInterface`介面，並對應至 20 虛擬方法表的位置。</span><span class="sxs-lookup"><span data-stu-id="d8546-113">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="d8546-114">若要能夠使用它們[ `CLRDATA_ADDRESS` ](../common-data-types-unmanaged-api-reference.md)必須定義為 64 位元不帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="d8546-114">To be able to use them, [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) must be defined as a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="d8546-115">需求</span><span class="sxs-lookup"><span data-stu-id="d8546-115">Requirements</span></span>

<span data-ttu-id="d8546-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d8546-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="d8546-117">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="d8546-117">**Header:** None</span></span>  
<span data-ttu-id="d8546-118">**程式庫：** 無</span><span class="sxs-lookup"><span data-stu-id="d8546-118">**Library:** None</span></span>  
<span data-ttu-id="d8546-119">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d8546-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="d8546-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8546-120">See also</span></span>

- [<span data-ttu-id="d8546-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="d8546-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="d8546-122">ISOSDacInterface 介面</span><span class="sxs-lookup"><span data-stu-id="d8546-122">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)