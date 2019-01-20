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
ms.openlocfilehash: ac4111abdf6a471aca1eca72a86e33698debbff6
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416328"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="5c753-102">IXCLRDataModule::GetVersionId 方法</span><span class="sxs-lookup"><span data-stu-id="5c753-102">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="5c753-103">取得模組的版本識別碼。</span><span class="sxs-lookup"><span data-stu-id="5c753-103">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="5c753-104">語法</span><span class="sxs-lookup"><span data-stu-id="5c753-104">Syntax</span></span>

```
HRESULT GetVersionId(
    [out] GUID* vid
);
```

### <a name="parameters"></a><span data-ttu-id="5c753-105">參數</span><span class="sxs-lookup"><span data-stu-id="5c753-105">Parameters</span></span>

<span data-ttu-id="5c753-106">`vid` [out]模組的版本識別碼。</span><span class="sxs-lookup"><span data-stu-id="5c753-106">`vid` [out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="5c753-107">備註</span><span class="sxs-lookup"><span data-stu-id="5c753-107">Remarks</span></span>

<span data-ttu-id="5c753-108">提供的方法是一部分`IXCLRDataModule`介面，並對應至的虛擬方法表 40 的位置。</span><span class="sxs-lookup"><span data-stu-id="5c753-108">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 40th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="5c753-109">需求</span><span class="sxs-lookup"><span data-stu-id="5c753-109">Requirements</span></span>

<span data-ttu-id="5c753-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5c753-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="5c753-111">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="5c753-111">**Header:** None</span></span>  
<span data-ttu-id="5c753-112">**程式庫：** 無</span><span class="sxs-lookup"><span data-stu-id="5c753-112">**Library:** None</span></span>  
<span data-ttu-id="5c753-113">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5c753-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="5c753-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c753-114">See Also</span></span>

- [<span data-ttu-id="5c753-115">偵錯</span><span class="sxs-lookup"><span data-stu-id="5c753-115">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="5c753-116">IXCLRDataModule 介面</span><span class="sxs-lookup"><span data-stu-id="5c753-116">IXCLRDataModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-interface.md)
