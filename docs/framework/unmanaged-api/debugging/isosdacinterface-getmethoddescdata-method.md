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
ms.openlocfilehash: e56f837c4d3362ec6e71030e4fb475df42b9fba4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54639941"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a><span data-ttu-id="9f6e2-102">ISOSDacInterface::GetMethodDescData 方法</span><span class="sxs-lookup"><span data-stu-id="9f6e2-102">ISOSDacInterface::GetMethodDescData Method</span></span>

<span data-ttu-id="9f6e2-103">取得的資料指定[MethodDesc](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="9f6e2-103">Gets the data for the given [MethodDesc](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="9f6e2-104">語法</span><span class="sxs-lookup"><span data-stu-id="9f6e2-104">Syntax</span></span>

```
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    void                       *data,
    ULONG                      cRevertedRejitVersions,
    void                      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

### <a name="parameters"></a><span data-ttu-id="9f6e2-105">參數</span><span class="sxs-lookup"><span data-stu-id="9f6e2-105">Parameters</span></span>

<span data-ttu-id="9f6e2-106">`methodDesc` [in]MethodDesc 位址。</span><span class="sxs-lookup"><span data-stu-id="9f6e2-106">`methodDesc` [in] The address of the MethodDesc.</span></span>

<span data-ttu-id="9f6e2-107">`ip` [in]方法的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="9f6e2-107">`ip` [in] The IP address of the method.</span></span>

<span data-ttu-id="9f6e2-108">`data` [out]傳回從內部 Api，與 MethodDesc 相關的資料。</span><span class="sxs-lookup"><span data-stu-id="9f6e2-108">`data` [out] The data associated with the MethodDesc as returned from the internal APIs.</span></span> <span data-ttu-id="9f6e2-109">結構必須至少 168 個位元組。</span><span class="sxs-lookup"><span data-stu-id="9f6e2-109">The structure needs at least 168 bytes.</span></span>

<span data-ttu-id="9f6e2-110">`cRevertedRejitVersions` [out]已還原的 rejit 版本數目。</span><span class="sxs-lookup"><span data-stu-id="9f6e2-110">`cRevertedRejitVersions` [out] The number of reverted rejit versions.</span></span>

<span data-ttu-id="9f6e2-111">`rgRevertedRejitData` [out]傳回的內部 Api，以還原的 rejit 版本相關聯的資料。</span><span class="sxs-lookup"><span data-stu-id="9f6e2-111">`rgRevertedRejitData` [out] The data associated with the reverted rejit versions as returned from the internal APIs.</span></span> <span data-ttu-id="9f6e2-112">結構必須至少在 24 個位元組。</span><span class="sxs-lookup"><span data-stu-id="9f6e2-112">The structure needs at least 24 bytes.</span></span>

<span data-ttu-id="9f6e2-113">`pcNeededRevertedRejitData` [out]儲存與還原的 ReJit 版本相關聯的資料所需的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="9f6e2-113">`pcNeededRevertedRejitData` [out] The number of bytes required to store the data associated with the reverted ReJit versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="9f6e2-114">備註</span><span class="sxs-lookup"><span data-stu-id="9f6e2-114">Remarks</span></span>

<span data-ttu-id="9f6e2-115">提供的方法是一部分`ISOSDacInterface`介面，並對應至 20 虛擬方法表的位置。</span><span class="sxs-lookup"><span data-stu-id="9f6e2-115">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="9f6e2-116">也`CLRDATA_ADDRESS`為 64 位元不帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="9f6e2-116">Also the `CLRDATA_ADDRESS` are 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="9f6e2-117">需求</span><span class="sxs-lookup"><span data-stu-id="9f6e2-117">Requirements</span></span>

<span data-ttu-id="9f6e2-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9f6e2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="9f6e2-119">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="9f6e2-119">**Header:** None</span></span>  
<span data-ttu-id="9f6e2-120">**程式庫：** 無</span><span class="sxs-lookup"><span data-stu-id="9f6e2-120">**Library:** None</span></span>  
<span data-ttu-id="9f6e2-121">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9f6e2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="9f6e2-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f6e2-122">See also</span></span>

- [<span data-ttu-id="9f6e2-123">偵錯</span><span class="sxs-lookup"><span data-stu-id="9f6e2-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="9f6e2-124">ISOSDacInterface 介面</span><span class="sxs-lookup"><span data-stu-id="9f6e2-124">ISOSDacInterface Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-interface.md)
