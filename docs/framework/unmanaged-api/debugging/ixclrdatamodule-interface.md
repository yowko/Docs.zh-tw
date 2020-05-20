---
title: IXCLRDataModule 介面
ms.date: 01/16/2019
api.name:
- IXCLRDataModule Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule Interface
helpviewer.keywords:
- IXCLRDataModule Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 3c2bc771c0a131329b9403c99a33ca7b79023771
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420847"
---
# <a name="ixclrdatamodule-interface"></a><span data-ttu-id="2d4f8-102">IXCLRDataModule 介面</span><span class="sxs-lookup"><span data-stu-id="2d4f8-102">IXCLRDataModule Interface</span></span>

<span data-ttu-id="2d4f8-103">提供方法來查詢已載入模組的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2d4f8-103">Provides methods for querying information about a loaded module.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="2d4f8-104">方法</span><span class="sxs-lookup"><span data-stu-id="2d4f8-104">Methods</span></span>

| <span data-ttu-id="2d4f8-105">方法</span><span class="sxs-lookup"><span data-stu-id="2d4f8-105">Method</span></span>                                                                                                                                | <span data-ttu-id="2d4f8-106">描述</span><span class="sxs-lookup"><span data-stu-id="2d4f8-106">Description</span></span>                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="2d4f8-107">GetMethodDefinitionByToken</span><span class="sxs-lookup"><span data-stu-id="2d4f8-107">GetMethodDefinitionByToken</span></span>](ixclrdatamodule-getmethoddefinitionbytoken-method.md) | <span data-ttu-id="2d4f8-108">取得對應至指定之元資料標記的方法定義。</span><span class="sxs-lookup"><span data-stu-id="2d4f8-108">Gets the method definition corresponding to a given metadata token.</span></span> |
| [<span data-ttu-id="2d4f8-109">邀請</span><span class="sxs-lookup"><span data-stu-id="2d4f8-109">Request</span></span>](ixclrdatamodule-request-method.md)                                       | <span data-ttu-id="2d4f8-110">要求填入模組資料所提供的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="2d4f8-110">Requests to populate the buffer given with the module's data.</span></span>       |
| [<span data-ttu-id="2d4f8-111">GetVersionId</span><span class="sxs-lookup"><span data-stu-id="2d4f8-111">GetVersionId</span></span>](ixclrdatamodule-getversionid-method.md)                             | <span data-ttu-id="2d4f8-112">取得模組的版本識別碼。</span><span class="sxs-lookup"><span data-stu-id="2d4f8-112">Gets the module's version ID.</span></span>                                       |

## <a name="remarks"></a><span data-ttu-id="2d4f8-113">備註</span><span class="sxs-lookup"><span data-stu-id="2d4f8-113">Remarks</span></span>

<span data-ttu-id="2d4f8-114">這個介面存在於執行時間內，而且不會透過任何標頭或程式庫檔案公開。</span><span class="sxs-lookup"><span data-stu-id="2d4f8-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="2d4f8-115">不過，它是衍生自的 COM 介面，其 `IUnknown` 具有 `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` 可透過一般 COM 機制取得的 GUID。</span><span class="sxs-lookup"><span data-stu-id="2d4f8-115">However, it's a COM interface that derives from `IUnknown` with GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="2d4f8-116">需求</span><span class="sxs-lookup"><span data-stu-id="2d4f8-116">Requirements</span></span>

<span data-ttu-id="2d4f8-117">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2d4f8-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="2d4f8-118">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="2d4f8-118">**Header:** None</span></span>  
<span data-ttu-id="2d4f8-119">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="2d4f8-119">**Library:** None</span></span>  
<span data-ttu-id="2d4f8-120">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2d4f8-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="2d4f8-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d4f8-121">See also</span></span>

- [<span data-ttu-id="2d4f8-122">偵錯</span><span class="sxs-lookup"><span data-stu-id="2d4f8-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="2d4f8-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="2d4f8-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
