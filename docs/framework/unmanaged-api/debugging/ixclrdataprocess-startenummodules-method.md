---
title: IXCLRDataProcess::StartEnumModules 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::StartEnumModules Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::StartEnumModules Method
helpviewer.keywords:
- IXCLRDataProcess::StartEnumModules Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 4a086157b27b7426cb6d5f17f13426c0f26d2b2d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658217"
---
# <a name="ixclrdataprocessstartenummodules-method"></a><span data-ttu-id="336b3-102">IXCLRDataProcess::StartEnumModules 方法</span><span class="sxs-lookup"><span data-stu-id="336b3-102">IXCLRDataProcess::StartEnumModules Method</span></span>

<span data-ttu-id="336b3-103">提供列舉的處理程序的模組控制代碼。</span><span class="sxs-lookup"><span data-stu-id="336b3-103">Provides a handle to enumerate the modules of a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="336b3-104">語法</span><span class="sxs-lookup"><span data-stu-id="336b3-104">Syntax</span></span>

```
HRESULT StartEnumModules(
    [out] CLRDATA_ENUM *handle
);
```

### <a name="parameters"></a><span data-ttu-id="336b3-105">參數</span><span class="sxs-lookup"><span data-stu-id="336b3-105">Parameters</span></span>

<span data-ttu-id="336b3-106">`handle` [out]列舉模組控制代碼。</span><span class="sxs-lookup"><span data-stu-id="336b3-106">`handle` [out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="336b3-107">備註</span><span class="sxs-lookup"><span data-stu-id="336b3-107">Remarks</span></span>

<span data-ttu-id="336b3-108">提供的方法是一部分`IXCLRDataProcess`介面，並對應至第 24 虛擬方法表的位置。</span><span class="sxs-lookup"><span data-stu-id="336b3-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 24th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="336b3-109">需求</span><span class="sxs-lookup"><span data-stu-id="336b3-109">Requirements</span></span>

<span data-ttu-id="336b3-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="336b3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="336b3-111">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="336b3-111">**Header:** None</span></span>  
<span data-ttu-id="336b3-112">**程式庫：** 無</span><span class="sxs-lookup"><span data-stu-id="336b3-112">**Library:** None</span></span>  
<span data-ttu-id="336b3-113">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="336b3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="336b3-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="336b3-114">See also</span></span>

- [<span data-ttu-id="336b3-115">CLRDataSourceType 列舉</span><span class="sxs-lookup"><span data-stu-id="336b3-115">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="336b3-116">偵錯</span><span class="sxs-lookup"><span data-stu-id="336b3-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="336b3-117">IXCLRDataProcess 介面</span><span class="sxs-lookup"><span data-stu-id="336b3-117">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
