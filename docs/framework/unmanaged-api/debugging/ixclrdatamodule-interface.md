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
ms.openlocfilehash: e306834166051ae48fd283d51f18d9458091578f
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416451"
---
# <a name="ixclrdatamodule-interface"></a><span data-ttu-id="44afd-102">IXCLRDataModule 介面</span><span class="sxs-lookup"><span data-stu-id="44afd-102">IXCLRDataModule Interface</span></span>

<span data-ttu-id="44afd-103">提供方法來查詢載入模組的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="44afd-103">Provides methods for querying information about a loaded module.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="44afd-104">方法</span><span class="sxs-lookup"><span data-stu-id="44afd-104">Methods</span></span>

| <span data-ttu-id="44afd-105">方法</span><span class="sxs-lookup"><span data-stu-id="44afd-105">Method</span></span>                                                                                                                                | <span data-ttu-id="44afd-106">描述</span><span class="sxs-lookup"><span data-stu-id="44afd-106">Description</span></span>                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="44afd-107">GetMethodDefinitionByToken</span><span class="sxs-lookup"><span data-stu-id="44afd-107">GetMethodDefinitionByToken</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-getmethoddefinitionbytoken-method.md) | <span data-ttu-id="44afd-108">取得對應至指定的中繼資料語彙基元的方法定義。</span><span class="sxs-lookup"><span data-stu-id="44afd-108">Gets the method definition corresponding to a given metadata token.</span></span> |
| [<span data-ttu-id="44afd-109">要求</span><span class="sxs-lookup"><span data-stu-id="44afd-109">Request</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-request-method.md)                                       | <span data-ttu-id="44afd-110">填入指定模組的資料緩衝區的要求。</span><span class="sxs-lookup"><span data-stu-id="44afd-110">Requests to populate the buffer given with the module's data.</span></span>       |
| [<span data-ttu-id="44afd-111">GetVersionId</span><span class="sxs-lookup"><span data-stu-id="44afd-111">GetVersionId</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-getversionid-method.md)                             | <span data-ttu-id="44afd-112">取得模組的版本識別碼。</span><span class="sxs-lookup"><span data-stu-id="44afd-112">Gets the module's version ID.</span></span>                                       |

## <a name="remarks"></a><span data-ttu-id="44afd-113">備註</span><span class="sxs-lookup"><span data-stu-id="44afd-113">Remarks</span></span>

<span data-ttu-id="44afd-114">此介面的執行階段內，而且不會公開透過任何標頭或程式庫檔案。</span><span class="sxs-lookup"><span data-stu-id="44afd-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="44afd-115">不過，它是 COM 介面衍生自`IUnknown`含有 GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` ，可以透過一般的 COM 機制取得。</span><span class="sxs-lookup"><span data-stu-id="44afd-115">However, it's a COM interface that derives from `IUnknown` with GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="44afd-116">需求</span><span class="sxs-lookup"><span data-stu-id="44afd-116">Requirements</span></span>

<span data-ttu-id="44afd-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="44afd-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="44afd-118">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="44afd-118">**Header:** None</span></span>  
<span data-ttu-id="44afd-119">**程式庫：** 無</span><span class="sxs-lookup"><span data-stu-id="44afd-119">**Library:** None</span></span>  
<span data-ttu-id="44afd-120">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="44afd-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="44afd-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44afd-121">See Also</span></span>

- [<span data-ttu-id="44afd-122">偵錯</span><span class="sxs-lookup"><span data-stu-id="44afd-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="44afd-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="44afd-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
