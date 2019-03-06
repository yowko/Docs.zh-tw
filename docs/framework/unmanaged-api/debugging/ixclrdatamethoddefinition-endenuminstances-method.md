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
ms.openlocfilehash: 28cd15a793d303e1d6e64c52c1d0095e8d619c7b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378926"
---
# <a name="ixclrdatamethoddefinitionendenuminstances-method"></a><span data-ttu-id="b7d3e-102">IXCLRDataMethodDefinition::EndEnumInstances 方法</span><span class="sxs-lookup"><span data-stu-id="b7d3e-102">IXCLRDataMethodDefinition::EndEnumInstances Method</span></span>

<span data-ttu-id="b7d3e-103">釋放執行個體列舉期間使用的內部迭代器所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="b7d3e-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="b7d3e-104">語法</span><span class="sxs-lookup"><span data-stu-id="b7d3e-104">Syntax</span></span>

```
HRESULT EndEnumInstances(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="b7d3e-105">參數</span><span class="sxs-lookup"><span data-stu-id="b7d3e-105">Parameters</span></span>

`handle`\
<span data-ttu-id="b7d3e-106">[out]列舉的執行個體控制代碼。</span><span class="sxs-lookup"><span data-stu-id="b7d3e-106">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="b7d3e-107">備註</span><span class="sxs-lookup"><span data-stu-id="b7d3e-107">Remarks</span></span>

<span data-ttu-id="b7d3e-108">提供的方法是一部分`IXCLRDataMethodDefinition`介面，而對應的虛擬方法表的第五個插槽。</span><span class="sxs-lookup"><span data-stu-id="b7d3e-108">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fifth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="b7d3e-109">需求</span><span class="sxs-lookup"><span data-stu-id="b7d3e-109">Requirements</span></span>

<span data-ttu-id="b7d3e-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b7d3e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="b7d3e-111">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="b7d3e-111">**Header:** None</span></span>  
<span data-ttu-id="b7d3e-112">**程式庫：** 無</span><span class="sxs-lookup"><span data-stu-id="b7d3e-112">**Library:** None</span></span>  
<span data-ttu-id="b7d3e-113">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b7d3e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="b7d3e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7d3e-114">See also</span></span>

- [<span data-ttu-id="b7d3e-115">偵錯</span><span class="sxs-lookup"><span data-stu-id="b7d3e-115">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="b7d3e-116">IXCLRDataMethodDefinition 介面</span><span class="sxs-lookup"><span data-stu-id="b7d3e-116">IXCLRDataMethodDefinition Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
