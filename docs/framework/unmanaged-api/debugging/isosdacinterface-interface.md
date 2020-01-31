---
title: ISOSDacInterface 介面
ms.date: 02/01/2019
api.name:
- ISOSDacInterface Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface Interface
helpviewer.keywords:
- ISOSDacInterface Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 94349a3f7b18c8ce29bb3a71cb9d10ee4eac8036
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790472"
---
# <a name="isosdacinterface-interface"></a><span data-ttu-id="b1ba8-102">ISOSDacInterface 介面</span><span class="sxs-lookup"><span data-stu-id="b1ba8-102">ISOSDacInterface Interface</span></span>

<span data-ttu-id="b1ba8-103">提供 helper 方法，以從 `SOS`存取資料。</span><span class="sxs-lookup"><span data-stu-id="b1ba8-103">Provides helper methods to access data from `SOS`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="b1ba8-104">方法</span><span class="sxs-lookup"><span data-stu-id="b1ba8-104">Methods</span></span>

| <span data-ttu-id="b1ba8-105">方法</span><span class="sxs-lookup"><span data-stu-id="b1ba8-105">Method</span></span>                                                                                                               | <span data-ttu-id="b1ba8-106">描述</span><span class="sxs-lookup"><span data-stu-id="b1ba8-106">Description</span></span>                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="b1ba8-107">GetMethodDescData</span><span class="sxs-lookup"><span data-stu-id="b1ba8-107">GetMethodDescData</span></span>](isosdacinterface-getmethoddescdata-method.md) | <span data-ttu-id="b1ba8-108">取得給定 MethodDesc 指標的資料。</span><span class="sxs-lookup"><span data-stu-id="b1ba8-108">Gets the data for the given MethodDesc pointer.</span></span> |
| [<span data-ttu-id="b1ba8-109">GetMethodDescPtrFromIP</span><span class="sxs-lookup"><span data-stu-id="b1ba8-109">GetMethodDescPtrFromIP</span></span>](isosdacinterface-getmethoddescptrfromip-method.md) | <span data-ttu-id="b1ba8-110">抓取 MethodDesc 的指標，其對應的方法包含指定的原生指令位址。</span><span class="sxs-lookup"><span data-stu-id="b1ba8-110">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span> |
| [<span data-ttu-id="b1ba8-111">GetModuleData</span><span class="sxs-lookup"><span data-stu-id="b1ba8-111">GetModuleData</span></span>](isosdacinterface-getmoduledata-method.md)| <span data-ttu-id="b1ba8-112">提取對應至在指定位址載入之模組的資料。</span><span class="sxs-lookup"><span data-stu-id="b1ba8-112">Fetches the data corresponding to the module loaded at a given address.</span></span> |

## <a name="remarks"></a><span data-ttu-id="b1ba8-113">備註</span><span class="sxs-lookup"><span data-stu-id="b1ba8-113">Remarks</span></span>

<span data-ttu-id="b1ba8-114">這個介面存在於執行時間內，而且不會透過任何標頭或程式庫檔案公開。</span><span class="sxs-lookup"><span data-stu-id="b1ba8-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="b1ba8-115">不過，它是衍生自 `IUnknown` 的 COM 介面，而 GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` 可透過一般的 COM 機制取得。</span><span class="sxs-lookup"><span data-stu-id="b1ba8-115">However, it's a COM interface that derives from `IUnknown` with GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="b1ba8-116">需求</span><span class="sxs-lookup"><span data-stu-id="b1ba8-116">Requirements</span></span>

<span data-ttu-id="b1ba8-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b1ba8-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="b1ba8-118">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="b1ba8-118">**Header:** None</span></span>  
<span data-ttu-id="b1ba8-119">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="b1ba8-119">**Library:** None</span></span>  
<span data-ttu-id="b1ba8-120">**.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b1ba8-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b1ba8-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="b1ba8-121">See also</span></span>

- [<span data-ttu-id="b1ba8-122">偵錯</span><span class="sxs-lookup"><span data-stu-id="b1ba8-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="b1ba8-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b1ba8-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
