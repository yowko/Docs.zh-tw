---
title: IXCLRDataMethodDefinition::StartEnumInstances 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::StartEnumInstances Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::StartEnumInstances Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::StartEnumInstances Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 208d6c46f18834b23e642efa82df0a365013a410
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416330"
---
# <a name="ixclrdatamethoddefinitionstartenuminstances-method"></a><span data-ttu-id="04901-102">IXCLRDataMethodDefinition::StartEnumInstances 方法</span><span class="sxs-lookup"><span data-stu-id="04901-102">IXCLRDataMethodDefinition::StartEnumInstances Method</span></span>

<span data-ttu-id="04901-103">提供的控制代碼的方法執行個體的列舉型別的指定`IXCLRDataAppDomain`。</span><span class="sxs-lookup"><span data-stu-id="04901-103">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="04901-104">語法</span><span class="sxs-lookup"><span data-stu-id="04901-104">Syntax</span></span>

```
HRESULT StartEnumInstances(
    [in] IXCLRDataAppDomain* appDomain,
    [out] CLRDATA_ENUM *handle
);
```

### <a name="parameters"></a><span data-ttu-id="04901-105">參數</span><span class="sxs-lookup"><span data-stu-id="04901-105">Parameters</span></span>

<span data-ttu-id="04901-106">`appDomain` [in]列舉型別的 AppDomain。</span><span class="sxs-lookup"><span data-stu-id="04901-106">`appDomain` [in] An AppDomain for the enumeration.</span></span>

<span data-ttu-id="04901-107">`handle` [out]列舉的執行個體控制代碼。</span><span class="sxs-lookup"><span data-stu-id="04901-107">`handle` [out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="04901-108">備註</span><span class="sxs-lookup"><span data-stu-id="04901-108">Remarks</span></span>

<span data-ttu-id="04901-109">提供的方法是一部分`IXCLRDataMethodDefinition`介面，並對應至第三個位置的虛擬方法表。</span><span class="sxs-lookup"><span data-stu-id="04901-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the third slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="04901-110">需求</span><span class="sxs-lookup"><span data-stu-id="04901-110">Requirements</span></span>

<span data-ttu-id="04901-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="04901-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="04901-112">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="04901-112">**Header:** None</span></span>  
<span data-ttu-id="04901-113">**程式庫：** 無</span><span class="sxs-lookup"><span data-stu-id="04901-113">**Library:** None</span></span>  
<span data-ttu-id="04901-114">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="04901-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="04901-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04901-115">See Also</span></span>

- [<span data-ttu-id="04901-116">CLRDataSourceType 列舉</span><span class="sxs-lookup"><span data-stu-id="04901-116">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="04901-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="04901-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="04901-118">IXCLRDataMethodDefinition 介面</span><span class="sxs-lookup"><span data-stu-id="04901-118">IXCLRDataMethodDefinition Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
