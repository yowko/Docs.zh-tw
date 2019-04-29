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
ms.openlocfilehash: e863f14676acc84f4d9f59d0898dee5b291bd30f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775436"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="3636b-102">IXCLRDataModule::GetVersionId 方法</span><span class="sxs-lookup"><span data-stu-id="3636b-102">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="3636b-103">取得模組的版本識別碼。</span><span class="sxs-lookup"><span data-stu-id="3636b-103">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="3636b-104">語法</span><span class="sxs-lookup"><span data-stu-id="3636b-104">Syntax</span></span>

```
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a><span data-ttu-id="3636b-105">參數</span><span class="sxs-lookup"><span data-stu-id="3636b-105">Parameters</span></span>

`vid`\
<span data-ttu-id="3636b-106">[out]模組的版本識別碼。</span><span class="sxs-lookup"><span data-stu-id="3636b-106">[out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="3636b-107">備註</span><span class="sxs-lookup"><span data-stu-id="3636b-107">Remarks</span></span>

<span data-ttu-id="3636b-108">提供的方法是一部分`IXCLRDataModule`介面，並對應至的虛擬方法表 40 的位置。</span><span class="sxs-lookup"><span data-stu-id="3636b-108">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 40th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="3636b-109">需求</span><span class="sxs-lookup"><span data-stu-id="3636b-109">Requirements</span></span>

<span data-ttu-id="3636b-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3636b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="3636b-111">**標頭：** None</span><span class="sxs-lookup"><span data-stu-id="3636b-111">**Header:** None</span></span>  
<span data-ttu-id="3636b-112">**LIBRARY:** None</span><span class="sxs-lookup"><span data-stu-id="3636b-112">**Library:** None</span></span>  
<span data-ttu-id="3636b-113">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3636b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="3636b-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3636b-114">See also</span></span>

- [<span data-ttu-id="3636b-115">偵錯</span><span class="sxs-lookup"><span data-stu-id="3636b-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="3636b-116">IXCLRDataModule 介面</span><span class="sxs-lookup"><span data-stu-id="3636b-116">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)