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
ms.openlocfilehash: dacf76582916ad50f51ae7c8818b496f31f9553e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353110"
---
# <a name="ixclrdatamethoddefinitionenuminstance-method"></a><span data-ttu-id="e4eca-102">IXCLRDataMethodDefinition::EnumInstance 方法</span><span class="sxs-lookup"><span data-stu-id="e4eca-102">IXCLRDataMethodDefinition::EnumInstance Method</span></span>

<span data-ttu-id="e4eca-103">列舉的執行個體，這個方法定義。</span><span class="sxs-lookup"><span data-stu-id="e4eca-103">Enumerates the instances of this method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="e4eca-104">語法</span><span class="sxs-lookup"><span data-stu-id="e4eca-104">Syntax</span></span>

```
HRESULT EnumInstance(
    [in, out] CLRDATA_ENUM         *handle,
    [out] IXCLRDataMethodInstance **instance
);
```

## <a name="parameters"></a><span data-ttu-id="e4eca-105">參數</span><span class="sxs-lookup"><span data-stu-id="e4eca-105">Parameters</span></span>

`handle`\
<span data-ttu-id="e4eca-106">[in、 out]列舉的執行個體控制代碼。</span><span class="sxs-lookup"><span data-stu-id="e4eca-106">[in, out] A handle for enumerating the instances.</span></span>

`instance`\
<span data-ttu-id="e4eca-107">[out]列舉的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e4eca-107">[out] The enumerated instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="e4eca-108">備註</span><span class="sxs-lookup"><span data-stu-id="e4eca-108">Remarks</span></span>

<span data-ttu-id="e4eca-109">提供的方法是一部分`IXCLRDataMethodDefinition`介面，而對應的虛擬方法表的第四個插槽。</span><span class="sxs-lookup"><span data-stu-id="e4eca-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="e4eca-110">需求</span><span class="sxs-lookup"><span data-stu-id="e4eca-110">Requirements</span></span>

<span data-ttu-id="e4eca-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e4eca-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="e4eca-112">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="e4eca-112">**Header:** None</span></span>  
<span data-ttu-id="e4eca-113">**程式庫：** 無</span><span class="sxs-lookup"><span data-stu-id="e4eca-113">**Library:** None</span></span>  
<span data-ttu-id="e4eca-114">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e4eca-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="e4eca-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4eca-115">See also</span></span>

- [<span data-ttu-id="e4eca-116">CLRDataSourceType 列舉</span><span class="sxs-lookup"><span data-stu-id="e4eca-116">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="e4eca-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="e4eca-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="e4eca-118">IXCLRDataMethodDefinition 介面</span><span class="sxs-lookup"><span data-stu-id="e4eca-118">IXCLRDataMethodDefinition Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
- [<span data-ttu-id="e4eca-119">IXCLRDataMethodInstance 介面</span><span class="sxs-lookup"><span data-stu-id="e4eca-119">IXCLRDataMethodInstance Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-interface.md)
