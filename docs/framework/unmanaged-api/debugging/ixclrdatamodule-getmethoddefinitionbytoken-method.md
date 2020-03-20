---
title: IXCLRData模組：獲取方法定義權杖方法
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::GetMethodDefinitionByToken Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::GetMethodDefinitionByToken Method
helpviewer.keywords:
- IXCLRDataModule::GetMethodDefinitionByToken Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 294c5340caf2217f9337d654a11a63a43d46febd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176665"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a><span data-ttu-id="61030-102">IXCLRData模組：獲取方法定義權杖方法</span><span class="sxs-lookup"><span data-stu-id="61030-102">IXCLRDataModule::GetMethodDefinitionByToken Method</span></span>

<span data-ttu-id="61030-103">獲取與給定中繼資料權杖對應的方法定義。</span><span class="sxs-lookup"><span data-stu-id="61030-103">Gets the method definition corresponding to a given metadata token.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="61030-104">語法</span><span class="sxs-lookup"><span data-stu-id="61030-104">Syntax</span></span>

```cpp
HRESULT GetMethodDefinitionByToken(
    [in] mdMethodDef token,
    [out] IXCLRDataMethodDefinition** methodDefinition
);
```

## <a name="parameters"></a><span data-ttu-id="61030-105">參數</span><span class="sxs-lookup"><span data-stu-id="61030-105">Parameters</span></span>

`token`\
<span data-ttu-id="61030-106">[在]方法權杖。</span><span class="sxs-lookup"><span data-stu-id="61030-106">[in] The method token.</span></span>

`methodDefinition`\
<span data-ttu-id="61030-107">[出]方法定義。</span><span class="sxs-lookup"><span data-stu-id="61030-107">[out] The method definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="61030-108">備註</span><span class="sxs-lookup"><span data-stu-id="61030-108">Remarks</span></span>

<span data-ttu-id="61030-109">提供的方法是介面的一`IXCLRDataModule`部分，對應于虛擬方法表的第 25 個插槽。</span><span class="sxs-lookup"><span data-stu-id="61030-109">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="61030-110">需求</span><span class="sxs-lookup"><span data-stu-id="61030-110">Requirements</span></span>

<span data-ttu-id="61030-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="61030-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="61030-112">**標題：** 沒有</span><span class="sxs-lookup"><span data-stu-id="61030-112">**Header:** None</span></span>  
<span data-ttu-id="61030-113">**庫：** 沒有</span><span class="sxs-lookup"><span data-stu-id="61030-113">**Library:** None</span></span>  
<span data-ttu-id="61030-114">**.NET 框架版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="61030-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="61030-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61030-115">See also</span></span>

- [<span data-ttu-id="61030-116">偵錯</span><span class="sxs-lookup"><span data-stu-id="61030-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="61030-117">IXCLRDataModule 介面</span><span class="sxs-lookup"><span data-stu-id="61030-117">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
