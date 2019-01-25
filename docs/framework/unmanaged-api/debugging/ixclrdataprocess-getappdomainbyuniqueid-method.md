---
title: IXCLRDataProcess::GetAppDomainByUniqueId 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::GetAppDomainByUniqueId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::GetAppDomainByUniqueId Method
helpviewer.keywords:
- IXCLRDataProcess::GetAppDomainByUniqueId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: cf610e3af26c60dd9bf738bff8785890394d0f34
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710270"
---
# <a name="ixclrdataprocessgetappdomainbyuniqueid-method"></a><span data-ttu-id="53c2e-102">IXCLRDataProcess::GetAppDomainByUniqueId 方法</span><span class="sxs-lookup"><span data-stu-id="53c2e-102">IXCLRDataProcess::GetAppDomainByUniqueId Method</span></span>

<span data-ttu-id="53c2e-103">取得`AppDomain`根據其唯一的識別項的處理序中。</span><span class="sxs-lookup"><span data-stu-id="53c2e-103">Gets an `AppDomain` in a process based on its unique identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="53c2e-104">語法</span><span class="sxs-lookup"><span data-stu-id="53c2e-104">Syntax</span></span>
```
HRESULT GetAppDomainByUniqueID(
    [in] ULONG64               id,
    [out] IXCLRDataAppDomain **appDomain
);
```

### <a name="parameters"></a><span data-ttu-id="53c2e-105">參數</span><span class="sxs-lookup"><span data-stu-id="53c2e-105">Parameters</span></span>
<span data-ttu-id="53c2e-106">`id` [in]AppDomain 的唯一識別碼</span><span class="sxs-lookup"><span data-stu-id="53c2e-106">`id` [in] The unique identifier of the AppDomain</span></span>

<span data-ttu-id="53c2e-107">`appDomain` [out]AppDomain</span><span class="sxs-lookup"><span data-stu-id="53c2e-107">`appDomain` [out] The AppDomain</span></span>

## <a name="remarks"></a><span data-ttu-id="53c2e-108">備註</span><span class="sxs-lookup"><span data-stu-id="53c2e-108">Remarks</span></span>

<span data-ttu-id="53c2e-109">提供的方法是一部分`IXCLRDataProcess`介面，並對應至 20 虛擬方法表的位置。</span><span class="sxs-lookup"><span data-stu-id="53c2e-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="53c2e-110">`IXCLRDataAppDomain*`傳回會用於與其他 Api 的互動。</span><span class="sxs-lookup"><span data-stu-id="53c2e-110">The `IXCLRDataAppDomain*` returned is used for interaction with other APIs.</span></span>

## <a name="requirements"></a><span data-ttu-id="53c2e-111">需求</span><span class="sxs-lookup"><span data-stu-id="53c2e-111">Requirements</span></span>
<span data-ttu-id="53c2e-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="53c2e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="53c2e-113">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="53c2e-113">**Header:** None</span></span>  
<span data-ttu-id="53c2e-114">**程式庫：** 無</span><span class="sxs-lookup"><span data-stu-id="53c2e-114">**Library:** None</span></span>  
<span data-ttu-id="53c2e-115">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="53c2e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="53c2e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53c2e-116">See also</span></span>
- [<span data-ttu-id="53c2e-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="53c2e-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="53c2e-118">IXCLRDataProcess 介面</span><span class="sxs-lookup"><span data-stu-id="53c2e-118">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
