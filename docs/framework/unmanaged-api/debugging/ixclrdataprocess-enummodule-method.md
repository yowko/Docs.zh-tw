---
title: IXCLRDataProcess::EnumModule 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumModule Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumModule Method
helpviewer.keywords:
- IXCLRDataProcess::EnumModule Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: a0398d18f9568754231082d63b4c6a2c865d8c6f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775261"
---
# <a name="ixclrdataprocessenummodule-method"></a><span data-ttu-id="9f2a4-102">IXCLRDataProcess::EnumModule 方法</span><span class="sxs-lookup"><span data-stu-id="9f2a4-102">IXCLRDataProcess::EnumModule Method</span></span>

<span data-ttu-id="9f2a4-103">列舉此程序的模組。</span><span class="sxs-lookup"><span data-stu-id="9f2a4-103">Enumerates the modules of this process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="9f2a4-104">語法</span><span class="sxs-lookup"><span data-stu-id="9f2a4-104">Syntax</span></span>

```
HRESULT EnumModule(
    [in, out] CLRDATA_ENUM  *handle,
    [out] IXCLRDataModule  **mod
);
```

## <a name="parameters"></a><span data-ttu-id="9f2a4-105">參數</span><span class="sxs-lookup"><span data-stu-id="9f2a4-105">Parameters</span></span>

`handle`\
<span data-ttu-id="9f2a4-106">[in、 out]列舉模組控制代碼。</span><span class="sxs-lookup"><span data-stu-id="9f2a4-106">[in, out] A handle for enumerating the modules.</span></span>

`mod`\
<span data-ttu-id="9f2a4-107">[out]列舉的模組中。</span><span class="sxs-lookup"><span data-stu-id="9f2a4-107">[out] The enumerated module.</span></span>

## <a name="remarks"></a><span data-ttu-id="9f2a4-108">備註</span><span class="sxs-lookup"><span data-stu-id="9f2a4-108">Remarks</span></span>

<span data-ttu-id="9f2a4-109">提供的方法是一部分`IXCLRDataProcess`介面，並對應至的虛擬方法表 25 的位置。</span><span class="sxs-lookup"><span data-stu-id="9f2a4-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="9f2a4-110">需求</span><span class="sxs-lookup"><span data-stu-id="9f2a4-110">Requirements</span></span>

<span data-ttu-id="9f2a4-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9f2a4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="9f2a4-112">**標頭：** None</span><span class="sxs-lookup"><span data-stu-id="9f2a4-112">**Header:** None</span></span>  
<span data-ttu-id="9f2a4-113">**LIBRARY:** None</span><span class="sxs-lookup"><span data-stu-id="9f2a4-113">**Library:** None</span></span>  
<span data-ttu-id="9f2a4-114">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9f2a4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="9f2a4-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f2a4-115">See also</span></span>

- [<span data-ttu-id="9f2a4-116">CLRDataSourceType 列舉</span><span class="sxs-lookup"><span data-stu-id="9f2a4-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="9f2a4-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="9f2a4-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="9f2a4-118">IXCLRDataModule 介面</span><span class="sxs-lookup"><span data-stu-id="9f2a4-118">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
- [<span data-ttu-id="9f2a4-119">IXCLRDataProcess 介面</span><span class="sxs-lookup"><span data-stu-id="9f2a4-119">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
