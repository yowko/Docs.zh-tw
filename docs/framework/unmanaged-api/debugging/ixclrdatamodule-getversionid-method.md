---
title: IXCLRDataModule::GetVersionId 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::GetVersionId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::GetVersionId Method
helpviewer.keywords:
- IXCLRDataModule::GetVersionId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 5bd84f784ea92e7b2ce2465e64972dc84e16a16c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744698"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="df2ab-102">IXCLRDataModule::GetVersionId 方法</span><span class="sxs-lookup"><span data-stu-id="df2ab-102">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="df2ab-103">取得模組的版本識別碼。</span><span class="sxs-lookup"><span data-stu-id="df2ab-103">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="df2ab-104">語法</span><span class="sxs-lookup"><span data-stu-id="df2ab-104">Syntax</span></span>

```cpp
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a><span data-ttu-id="df2ab-105">參數</span><span class="sxs-lookup"><span data-stu-id="df2ab-105">Parameters</span></span>

`vid`\
<span data-ttu-id="df2ab-106">[out]模組的版本識別碼。</span><span class="sxs-lookup"><span data-stu-id="df2ab-106">[out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="df2ab-107">備註</span><span class="sxs-lookup"><span data-stu-id="df2ab-107">Remarks</span></span>

<span data-ttu-id="df2ab-108">提供的方法是一部分`IXCLRDataModule`介面，並對應至的虛擬方法表 40 的位置。</span><span class="sxs-lookup"><span data-stu-id="df2ab-108">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 40th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="df2ab-109">需求</span><span class="sxs-lookup"><span data-stu-id="df2ab-109">Requirements</span></span>

<span data-ttu-id="df2ab-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="df2ab-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="df2ab-111">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="df2ab-111">**Header:** None</span></span>  
<span data-ttu-id="df2ab-112">**LIBRARY:** None</span><span class="sxs-lookup"><span data-stu-id="df2ab-112">**Library:** None</span></span>  
<span data-ttu-id="df2ab-113">**.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="df2ab-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="df2ab-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df2ab-114">See also</span></span>

- [<span data-ttu-id="df2ab-115">偵錯</span><span class="sxs-lookup"><span data-stu-id="df2ab-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="df2ab-116">IXCLRDataModule 介面</span><span class="sxs-lookup"><span data-stu-id="df2ab-116">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
