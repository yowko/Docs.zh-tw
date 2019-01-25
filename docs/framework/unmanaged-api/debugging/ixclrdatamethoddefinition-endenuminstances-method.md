---
title: IXCLRDataMethodDefinition::EndEnumInstances 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::EndEnumInstances Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::EndEnumInstances Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::EndEnumInstances Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 4a7cd8850778e9bbbc7d8d67f464c7787e40bc13
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566087"
---
# <a name="ixclrdatamethoddefinitionendenuminstances-method"></a><span data-ttu-id="a5b5d-102">IXCLRDataMethodDefinition::EndEnumInstances 方法</span><span class="sxs-lookup"><span data-stu-id="a5b5d-102">IXCLRDataMethodDefinition::EndEnumInstances Method</span></span>

<span data-ttu-id="a5b5d-103">釋放執行個體列舉期間使用的內部迭代器所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="a5b5d-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="a5b5d-104">語法</span><span class="sxs-lookup"><span data-stu-id="a5b5d-104">Syntax</span></span>

```
HRESULT EndEnumInstances(
    [in] CLRDATA_ENUM handle
);
```

### <a name="parameters"></a><span data-ttu-id="a5b5d-105">參數</span><span class="sxs-lookup"><span data-stu-id="a5b5d-105">Parameters</span></span>

<span data-ttu-id="a5b5d-106">`handle` [out]列舉的執行個體控制代碼。</span><span class="sxs-lookup"><span data-stu-id="a5b5d-106">`handle` [out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="a5b5d-107">備註</span><span class="sxs-lookup"><span data-stu-id="a5b5d-107">Remarks</span></span>

<span data-ttu-id="a5b5d-108">提供的方法是一部分`IXCLRDataMethodDefinition`介面，而對應的虛擬方法表的第五個插槽。</span><span class="sxs-lookup"><span data-stu-id="a5b5d-108">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fifth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="a5b5d-109">需求</span><span class="sxs-lookup"><span data-stu-id="a5b5d-109">Requirements</span></span>

<span data-ttu-id="a5b5d-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a5b5d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="a5b5d-111">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="a5b5d-111">**Header:** None</span></span>  
<span data-ttu-id="a5b5d-112">**程式庫：** 無</span><span class="sxs-lookup"><span data-stu-id="a5b5d-112">**Library:** None</span></span>  
<span data-ttu-id="a5b5d-113">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a5b5d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="a5b5d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5b5d-114">See also</span></span>

- [<span data-ttu-id="a5b5d-115">偵錯</span><span class="sxs-lookup"><span data-stu-id="a5b5d-115">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="a5b5d-116">IXCLRDataMethodDefinition 介面</span><span class="sxs-lookup"><span data-stu-id="a5b5d-116">IXCLRDataMethodDefinition Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
