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
ms.openlocfilehash: 41b6ff0a3c44d3ad997c54b1c82590cc3583fe52
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775228"
---
# <a name="ixclrdataprocessstartenummethodinstancesbyaddress-method"></a><span data-ttu-id="0c7c2-102">IXCLRDataProcess::StartEnumMethodInstancesByAddress 方法</span><span class="sxs-lookup"><span data-stu-id="0c7c2-102">IXCLRDataProcess::StartEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="0c7c2-103">提供列舉的方法執行個體的控制代碼`AppDomain`指定位址開頭。</span><span class="sxs-lookup"><span data-stu-id="0c7c2-103">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="0c7c2-104">語法</span><span class="sxs-lookup"><span data-stu-id="0c7c2-104">Syntax</span></span>

```
HRESULT StartEnumMethodInstancesByAddress(
    [in] CLRDATA_ADDRESS     address,
    [in] IXCLRDataAppDomain *appDomain,
    [out] CLRDATA_ENUM      *handle
);
```

## <a name="parameters"></a><span data-ttu-id="0c7c2-105">參數</span><span class="sxs-lookup"><span data-stu-id="0c7c2-105">Parameters</span></span>

`address`\
<span data-ttu-id="0c7c2-106">[in]第一個方法執行個體的位址。</span><span class="sxs-lookup"><span data-stu-id="0c7c2-106">[in] The address of the first method instance.</span></span>

`appDomain`\
<span data-ttu-id="0c7c2-107">[in]方法執行個體的 AppDomain。</span><span class="sxs-lookup"><span data-stu-id="0c7c2-107">[in] The AppDomain of the method instances.</span></span>

`handle`\
<span data-ttu-id="0c7c2-108">[out]列舉的方法執行個體控制代碼。</span><span class="sxs-lookup"><span data-stu-id="0c7c2-108">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="0c7c2-109">備註</span><span class="sxs-lookup"><span data-stu-id="0c7c2-109">Remarks</span></span>

<span data-ttu-id="0c7c2-110">提供的方法是一部分`IXCLRDataProcess`介面，並對應至的虛擬方法表 27 的位置。</span><span class="sxs-lookup"><span data-stu-id="0c7c2-110">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 27th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="0c7c2-111">需求</span><span class="sxs-lookup"><span data-stu-id="0c7c2-111">Requirements</span></span>

<span data-ttu-id="0c7c2-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0c7c2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="0c7c2-113">**標頭：** None</span><span class="sxs-lookup"><span data-stu-id="0c7c2-113">**Header:** None</span></span>  
<span data-ttu-id="0c7c2-114">**LIBRARY:** None</span><span class="sxs-lookup"><span data-stu-id="0c7c2-114">**Library:** None</span></span>  
<span data-ttu-id="0c7c2-115">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0c7c2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="0c7c2-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c7c2-116">See also</span></span>

- [<span data-ttu-id="0c7c2-117">CLRDataSourceType 列舉</span><span class="sxs-lookup"><span data-stu-id="0c7c2-117">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="0c7c2-118">偵錯</span><span class="sxs-lookup"><span data-stu-id="0c7c2-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="0c7c2-119">IXCLRDataProcess 介面</span><span class="sxs-lookup"><span data-stu-id="0c7c2-119">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
