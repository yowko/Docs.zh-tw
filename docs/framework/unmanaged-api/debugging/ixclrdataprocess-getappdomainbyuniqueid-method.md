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
ms.openlocfilehash: 8b468d40ef8eb523ba8881627fae15cf9b7c7b80
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775254"
---
# <a name="ixclrdataprocessgetappdomainbyuniqueid-method"></a><span data-ttu-id="03a1f-102">IXCLRDataProcess::GetAppDomainByUniqueId 方法</span><span class="sxs-lookup"><span data-stu-id="03a1f-102">IXCLRDataProcess::GetAppDomainByUniqueId Method</span></span>

<span data-ttu-id="03a1f-103">取得`AppDomain`根據其唯一的識別項的處理序中。</span><span class="sxs-lookup"><span data-stu-id="03a1f-103">Gets an `AppDomain` in a process based on its unique identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="03a1f-104">語法</span><span class="sxs-lookup"><span data-stu-id="03a1f-104">Syntax</span></span>

```cpp
HRESULT GetAppDomainByUniqueID(
    [in] ULONG64               id,
    [out] IXCLRDataAppDomain **appDomain
);
```

## <a name="parameters"></a><span data-ttu-id="03a1f-105">參數</span><span class="sxs-lookup"><span data-stu-id="03a1f-105">Parameters</span></span>

`id`\
<span data-ttu-id="03a1f-106">[in]AppDomain 的唯一識別碼</span><span class="sxs-lookup"><span data-stu-id="03a1f-106">[in] The unique identifier of the AppDomain</span></span>

`appDomain`\
<span data-ttu-id="03a1f-107">[out]AppDomain</span><span class="sxs-lookup"><span data-stu-id="03a1f-107">[out] The AppDomain</span></span>

## <a name="remarks"></a><span data-ttu-id="03a1f-108">備註</span><span class="sxs-lookup"><span data-stu-id="03a1f-108">Remarks</span></span>

<span data-ttu-id="03a1f-109">提供的方法是一部分`IXCLRDataProcess`介面，並對應至 20 虛擬方法表的位置。</span><span class="sxs-lookup"><span data-stu-id="03a1f-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="03a1f-110">`IXCLRDataAppDomain*`傳回會用於與其他 Api 的互動。</span><span class="sxs-lookup"><span data-stu-id="03a1f-110">The `IXCLRDataAppDomain*` returned is used for interaction with other APIs.</span></span>

## <a name="requirements"></a><span data-ttu-id="03a1f-111">需求</span><span class="sxs-lookup"><span data-stu-id="03a1f-111">Requirements</span></span>

<span data-ttu-id="03a1f-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="03a1f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>
<span data-ttu-id="03a1f-113">**標頭：** 無**程式庫：** 無 **.NET Framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="03a1f-113">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="03a1f-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03a1f-114">See also</span></span>

- [<span data-ttu-id="03a1f-115">偵錯</span><span class="sxs-lookup"><span data-stu-id="03a1f-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="03a1f-116">IXCLRDataProcess 介面</span><span class="sxs-lookup"><span data-stu-id="03a1f-116">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
