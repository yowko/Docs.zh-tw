---
title: IXCLRDataMethodDefinition::EnumInstance 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::EnumInstance Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::EnumInstance Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::EnumInstance Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 0fbb246f8c4bf791dd705aedf8eab6ef8bfeae56
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680256"
---
# <a name="ixclrdatamethoddefinitionenuminstance-method"></a><span data-ttu-id="7668f-102">IXCLRDataMethodDefinition::EnumInstance 方法</span><span class="sxs-lookup"><span data-stu-id="7668f-102">IXCLRDataMethodDefinition::EnumInstance Method</span></span>

<span data-ttu-id="7668f-103">列舉的執行個體，這個方法定義。</span><span class="sxs-lookup"><span data-stu-id="7668f-103">Enumerates the instances of this method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="7668f-104">語法</span><span class="sxs-lookup"><span data-stu-id="7668f-104">Syntax</span></span>

```
HRESULT EnumInstance(
    [in, out] CLRDATA_ENUM         *handle,
    [out] IXCLRDataMethodInstance **instance
);
```

### <a name="parameters"></a><span data-ttu-id="7668f-105">參數</span><span class="sxs-lookup"><span data-stu-id="7668f-105">Parameters</span></span>

<span data-ttu-id="7668f-106">`handle` [in、 out]列舉的執行個體控制代碼。</span><span class="sxs-lookup"><span data-stu-id="7668f-106">`handle` [in, out] A handle for enumerating the instances.</span></span>

<span data-ttu-id="7668f-107">`instance` [out]列舉的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7668f-107">`instance` [out] The enumerated instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="7668f-108">備註</span><span class="sxs-lookup"><span data-stu-id="7668f-108">Remarks</span></span>

<span data-ttu-id="7668f-109">提供的方法是一部分`IXCLRDataMethodDefinition`介面，而對應的虛擬方法表的第四個插槽。</span><span class="sxs-lookup"><span data-stu-id="7668f-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="7668f-110">需求</span><span class="sxs-lookup"><span data-stu-id="7668f-110">Requirements</span></span>

<span data-ttu-id="7668f-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7668f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="7668f-112">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="7668f-112">**Header:** None</span></span>  
<span data-ttu-id="7668f-113">**程式庫：** 無</span><span class="sxs-lookup"><span data-stu-id="7668f-113">**Library:** None</span></span>  
<span data-ttu-id="7668f-114">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7668f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="7668f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7668f-115">See also</span></span>

- [<span data-ttu-id="7668f-116">CLRDataSourceType 列舉</span><span class="sxs-lookup"><span data-stu-id="7668f-116">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="7668f-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="7668f-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="7668f-118">IXCLRDataMethodDefinition 介面</span><span class="sxs-lookup"><span data-stu-id="7668f-118">IXCLRDataMethodDefinition Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
- [<span data-ttu-id="7668f-119">IXCLRDataMethodInstance 介面</span><span class="sxs-lookup"><span data-stu-id="7668f-119">IXCLRDataMethodInstance Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-interface.md)
