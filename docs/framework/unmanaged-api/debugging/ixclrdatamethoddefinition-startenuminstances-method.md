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
ms.openlocfilehash: e92eea9677731756bdbfcbdcfac1531861fb5dce
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57361339"
---
# <a name="ixclrdatamethoddefinitionstartenuminstances-method"></a><span data-ttu-id="96793-102">IXCLRDataMethodDefinition::StartEnumInstances 方法</span><span class="sxs-lookup"><span data-stu-id="96793-102">IXCLRDataMethodDefinition::StartEnumInstances Method</span></span>

<span data-ttu-id="96793-103">提供的控制代碼的方法執行個體的列舉型別的指定`IXCLRDataAppDomain`。</span><span class="sxs-lookup"><span data-stu-id="96793-103">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="96793-104">語法</span><span class="sxs-lookup"><span data-stu-id="96793-104">Syntax</span></span>

```
HRESULT StartEnumInstances(
    [in] IXCLRDataAppDomain* appDomain,
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="96793-105">參數</span><span class="sxs-lookup"><span data-stu-id="96793-105">Parameters</span></span>

`appDomain`\
<span data-ttu-id="96793-106">[in]列舉型別的 AppDomain。</span><span class="sxs-lookup"><span data-stu-id="96793-106">[in] An AppDomain for the enumeration.</span></span>

`handle`\
<span data-ttu-id="96793-107">[out]列舉的執行個體控制代碼。</span><span class="sxs-lookup"><span data-stu-id="96793-107">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="96793-108">備註</span><span class="sxs-lookup"><span data-stu-id="96793-108">Remarks</span></span>

<span data-ttu-id="96793-109">提供的方法是一部分`IXCLRDataMethodDefinition`介面，並對應至第三個位置的虛擬方法表。</span><span class="sxs-lookup"><span data-stu-id="96793-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the third slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="96793-110">需求</span><span class="sxs-lookup"><span data-stu-id="96793-110">Requirements</span></span>

<span data-ttu-id="96793-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="96793-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="96793-112">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="96793-112">**Header:** None</span></span>  
<span data-ttu-id="96793-113">**程式庫：** 無</span><span class="sxs-lookup"><span data-stu-id="96793-113">**Library:** None</span></span>  
<span data-ttu-id="96793-114">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="96793-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="96793-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96793-115">See also</span></span>

- [<span data-ttu-id="96793-116">CLRDataSourceType 列舉</span><span class="sxs-lookup"><span data-stu-id="96793-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="96793-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="96793-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="96793-118">IXCLRDataMethodDefinition 介面</span><span class="sxs-lookup"><span data-stu-id="96793-118">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)