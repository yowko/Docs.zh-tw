---
title: IXCLRDataProcess::StartEnumMethodInstancesByAddress 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 9afbf0665b114169661a74b60c744203d160fed3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662617"
---
# <a name="ixclrdataprocessstartenummethodinstancesbyaddress-method"></a><span data-ttu-id="be77b-102">IXCLRDataProcess::StartEnumMethodInstancesByAddress 方法</span><span class="sxs-lookup"><span data-stu-id="be77b-102">IXCLRDataProcess::StartEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="be77b-103">提供列舉的方法執行個體的控制代碼`AppDomain`指定位址開頭。</span><span class="sxs-lookup"><span data-stu-id="be77b-103">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="be77b-104">語法</span><span class="sxs-lookup"><span data-stu-id="be77b-104">Syntax</span></span>

```
HRESULT StartEnumMethodInstancesByAddress(
    [in] CLRDATA_ADDRESS     address,
    [in] IXCLRDataAppDomain *appDomain,
    [out] CLRDATA_ENUM      *handle
);
```

### <a name="parameters"></a><span data-ttu-id="be77b-105">參數</span><span class="sxs-lookup"><span data-stu-id="be77b-105">Parameters</span></span>

<span data-ttu-id="be77b-106">`address` [in]第一個方法執行個體的位址。</span><span class="sxs-lookup"><span data-stu-id="be77b-106">`address` [in] The address of the first method instance.</span></span>

<span data-ttu-id="be77b-107">`appDomain` [in]方法執行個體的 AppDomain。</span><span class="sxs-lookup"><span data-stu-id="be77b-107">`appDomain` [in] The AppDomain of the method instances.</span></span>

<span data-ttu-id="be77b-108">`handle` [out]列舉的方法執行個體控制代碼。</span><span class="sxs-lookup"><span data-stu-id="be77b-108">`handle` [out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="be77b-109">備註</span><span class="sxs-lookup"><span data-stu-id="be77b-109">Remarks</span></span>

<span data-ttu-id="be77b-110">提供的方法是一部分`IXCLRDataProcess`介面，並對應至的虛擬方法表 27 的位置。</span><span class="sxs-lookup"><span data-stu-id="be77b-110">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 27th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="be77b-111">需求</span><span class="sxs-lookup"><span data-stu-id="be77b-111">Requirements</span></span>

<span data-ttu-id="be77b-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="be77b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="be77b-113">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="be77b-113">**Header:** None</span></span>  
<span data-ttu-id="be77b-114">**程式庫：** 無</span><span class="sxs-lookup"><span data-stu-id="be77b-114">**Library:** None</span></span>  
<span data-ttu-id="be77b-115">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="be77b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="be77b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be77b-116">See also</span></span>

- [<span data-ttu-id="be77b-117">CLRDataSourceType 列舉</span><span class="sxs-lookup"><span data-stu-id="be77b-117">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="be77b-118">偵錯</span><span class="sxs-lookup"><span data-stu-id="be77b-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="be77b-119">IXCLRDataProcess 介面</span><span class="sxs-lookup"><span data-stu-id="be77b-119">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
