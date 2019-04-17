---
title: IXCLRDataProcess::EndEnumModules 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumModules Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumModules Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumModules Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: de30384b4c12c4fcac3eafe580484685f8a43fa4
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2019
ms.locfileid: "59611428"
---
# <a name="ixclrdataprocessendenummodules-method"></a><span data-ttu-id="a6a3d-102">IXCLRDataProcess::EndEnumModules 方法</span><span class="sxs-lookup"><span data-stu-id="a6a3d-102">IXCLRDataProcess::EndEnumModules Method</span></span>

<span data-ttu-id="a6a3d-103">釋出內部模組列舉期間使用的迭代器所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="a6a3d-103">Releases the resources used by internal iterators used during module enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="a6a3d-104">語法</span><span class="sxs-lookup"><span data-stu-id="a6a3d-104">Syntax</span></span>

```cpp
HRESULT EndEnumModules(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="a6a3d-105">參數</span><span class="sxs-lookup"><span data-stu-id="a6a3d-105">Parameters</span></span>

`handle`\
<span data-ttu-id="a6a3d-106">[out]列舉模組控制代碼。</span><span class="sxs-lookup"><span data-stu-id="a6a3d-106">[out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="a6a3d-107">備註</span><span class="sxs-lookup"><span data-stu-id="a6a3d-107">Remarks</span></span>

<span data-ttu-id="a6a3d-108">提供的方法是一部分`IXCLRDataProcess`介面，並對應至的虛擬方法表 26 的位置。</span><span class="sxs-lookup"><span data-stu-id="a6a3d-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 26th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="a6a3d-109">需求</span><span class="sxs-lookup"><span data-stu-id="a6a3d-109">Requirements</span></span>

<span data-ttu-id="a6a3d-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a6a3d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>
<span data-ttu-id="a6a3d-111">**標頭：** 無**程式庫：** 無 **.NET Framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a6a3d-111">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a6a3d-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6a3d-112">See also</span></span>

- [<span data-ttu-id="a6a3d-113">偵錯</span><span class="sxs-lookup"><span data-stu-id="a6a3d-113">Debugging</span></span>](index.md)
- [<span data-ttu-id="a6a3d-114">IXCLRDataProcess 介面</span><span class="sxs-lookup"><span data-stu-id="a6a3d-114">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
