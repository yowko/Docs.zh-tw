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
ms.openlocfilehash: a81da147c1483e7649612050f4aba29a2cc63b49
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416481"
---
# <a name="ixclrdataprocessstartenummodules-method"></a><span data-ttu-id="cda1f-102">IXCLRDataProcess::StartEnumModules 方法</span><span class="sxs-lookup"><span data-stu-id="cda1f-102">IXCLRDataProcess::StartEnumModules Method</span></span>

<span data-ttu-id="cda1f-103">提供列舉的處理程序的模組控制代碼。</span><span class="sxs-lookup"><span data-stu-id="cda1f-103">Provides a handle to enumerate the modules of a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="cda1f-104">語法</span><span class="sxs-lookup"><span data-stu-id="cda1f-104">Syntax</span></span>

```
HRESULT StartEnumModules(
    [out] CLRDATA_ENUM *handle
);
```

### <a name="parameters"></a><span data-ttu-id="cda1f-105">參數</span><span class="sxs-lookup"><span data-stu-id="cda1f-105">Parameters</span></span>

<span data-ttu-id="cda1f-106">`handle` [out]列舉模組控制代碼。</span><span class="sxs-lookup"><span data-stu-id="cda1f-106">`handle` [out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="cda1f-107">備註</span><span class="sxs-lookup"><span data-stu-id="cda1f-107">Remarks</span></span>

<span data-ttu-id="cda1f-108">提供的方法是一部分`IXCLRDataProcess`介面，並對應至第 24 虛擬方法表的位置。</span><span class="sxs-lookup"><span data-stu-id="cda1f-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 24th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="cda1f-109">需求</span><span class="sxs-lookup"><span data-stu-id="cda1f-109">Requirements</span></span>

<span data-ttu-id="cda1f-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cda1f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="cda1f-111">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="cda1f-111">**Header:** None</span></span>  
<span data-ttu-id="cda1f-112">**程式庫：** 無</span><span class="sxs-lookup"><span data-stu-id="cda1f-112">**Library:** None</span></span>  
<span data-ttu-id="cda1f-113">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cda1f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="cda1f-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cda1f-114">See Also</span></span>

- [<span data-ttu-id="cda1f-115">CLRDataSourceType 列舉</span><span class="sxs-lookup"><span data-stu-id="cda1f-115">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="cda1f-116">偵錯</span><span class="sxs-lookup"><span data-stu-id="cda1f-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="cda1f-117">IXCLRDataProcess 介面</span><span class="sxs-lookup"><span data-stu-id="cda1f-117">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
