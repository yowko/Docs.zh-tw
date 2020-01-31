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
ms.openlocfilehash: 8757642db6c4375cf55d1f7288669c4c8a752a38
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790398"
---
# <a name="ixclrdatamodule-interface"></a><span data-ttu-id="738e5-102">IXCLRDataModule 介面</span><span class="sxs-lookup"><span data-stu-id="738e5-102">IXCLRDataModule Interface</span></span>

<span data-ttu-id="738e5-103">提供方法來查詢已載入模組的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="738e5-103">Provides methods for querying information about a loaded module.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="738e5-104">方法</span><span class="sxs-lookup"><span data-stu-id="738e5-104">Methods</span></span>

| <span data-ttu-id="738e5-105">方法</span><span class="sxs-lookup"><span data-stu-id="738e5-105">Method</span></span>                                                                                                                                | <span data-ttu-id="738e5-106">描述</span><span class="sxs-lookup"><span data-stu-id="738e5-106">Description</span></span>                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="738e5-107">GetMethodDefinitionByToken</span><span class="sxs-lookup"><span data-stu-id="738e5-107">GetMethodDefinitionByToken</span></span>](ixclrdatamodule-getmethoddefinitionbytoken-method.md) | <span data-ttu-id="738e5-108">取得對應至指定之元資料標記的方法定義。</span><span class="sxs-lookup"><span data-stu-id="738e5-108">Gets the method definition corresponding to a given metadata token.</span></span> |
| [<span data-ttu-id="738e5-109">要求</span><span class="sxs-lookup"><span data-stu-id="738e5-109">Request</span></span>](ixclrdatamodule-request-method.md)                                       | <span data-ttu-id="738e5-110">要求填入模組資料所提供的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="738e5-110">Requests to populate the buffer given with the module's data.</span></span>       |
| [<span data-ttu-id="738e5-111">GetVersionId</span><span class="sxs-lookup"><span data-stu-id="738e5-111">GetVersionId</span></span>](ixclrdatamodule-getversionid-method.md)                             | <span data-ttu-id="738e5-112">取得模組的版本識別碼。</span><span class="sxs-lookup"><span data-stu-id="738e5-112">Gets the module's version ID.</span></span>                                       |

## <a name="remarks"></a><span data-ttu-id="738e5-113">備註</span><span class="sxs-lookup"><span data-stu-id="738e5-113">Remarks</span></span>

<span data-ttu-id="738e5-114">這個介面存在於執行時間內，而且不會透過任何標頭或程式庫檔案公開。</span><span class="sxs-lookup"><span data-stu-id="738e5-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="738e5-115">不過，它是衍生自 `IUnknown` 的 COM 介面，而 GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` 可透過一般的 COM 機制取得。</span><span class="sxs-lookup"><span data-stu-id="738e5-115">However, it's a COM interface that derives from `IUnknown` with GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="738e5-116">需求</span><span class="sxs-lookup"><span data-stu-id="738e5-116">Requirements</span></span>

<span data-ttu-id="738e5-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="738e5-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="738e5-118">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="738e5-118">**Header:** None</span></span>  
<span data-ttu-id="738e5-119">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="738e5-119">**Library:** None</span></span>  
<span data-ttu-id="738e5-120">**.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="738e5-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="738e5-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="738e5-121">See also</span></span>

- [<span data-ttu-id="738e5-122">偵錯</span><span class="sxs-lookup"><span data-stu-id="738e5-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="738e5-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="738e5-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
