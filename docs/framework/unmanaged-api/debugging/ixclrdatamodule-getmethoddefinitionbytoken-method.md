---
title: IXCLRDataModule::GetMethodDefinitionByToken 方法
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
ms.openlocfilehash: 27f1ee28aff95340d4b533473b2f699a9405c3a2
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416494"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a><span data-ttu-id="0680d-102">IXCLRDataModule::GetMethodDefinitionByToken 方法</span><span class="sxs-lookup"><span data-stu-id="0680d-102">IXCLRDataModule::GetMethodDefinitionByToken Method</span></span>

<span data-ttu-id="0680d-103">取得對應至指定的中繼資料語彙基元的方法定義。</span><span class="sxs-lookup"><span data-stu-id="0680d-103">Gets the method definition corresponding to a given metadata token.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="0680d-104">語法</span><span class="sxs-lookup"><span data-stu-id="0680d-104">Syntax</span></span>

```
HRESULT GetMethodDefinitionByToken(
    [in] mdMethodDef token,
    [out] IXCLRDataMethodDefinition** methodDefinition
);
```

### <a name="parameters"></a><span data-ttu-id="0680d-105">參數</span><span class="sxs-lookup"><span data-stu-id="0680d-105">Parameters</span></span>

<span data-ttu-id="0680d-106">`token` [in]方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="0680d-106">`token` [in] The method token.</span></span>

<span data-ttu-id="0680d-107">`methodDefinition` [out]方法定義。</span><span class="sxs-lookup"><span data-stu-id="0680d-107">`methodDefinition` [out] The method definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="0680d-108">備註</span><span class="sxs-lookup"><span data-stu-id="0680d-108">Remarks</span></span>

<span data-ttu-id="0680d-109">提供的方法是一部分`IXCLRDataModule`介面，並對應至的虛擬方法表 25 的位置。</span><span class="sxs-lookup"><span data-stu-id="0680d-109">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="0680d-110">需求</span><span class="sxs-lookup"><span data-stu-id="0680d-110">Requirements</span></span>

<span data-ttu-id="0680d-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0680d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="0680d-112">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="0680d-112">**Header:** None</span></span>  
<span data-ttu-id="0680d-113">**程式庫：** 無</span><span class="sxs-lookup"><span data-stu-id="0680d-113">**Library:** None</span></span>  
<span data-ttu-id="0680d-114">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0680d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
 
## <a name="see-also"></a><span data-ttu-id="0680d-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0680d-115">See Also</span></span>

- [<span data-ttu-id="0680d-116">偵錯</span><span class="sxs-lookup"><span data-stu-id="0680d-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="0680d-117">IXCLRDataModule 介面</span><span class="sxs-lookup"><span data-stu-id="0680d-117">IXCLRDataModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-interface.md)
