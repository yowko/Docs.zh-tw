---
title: ISOSDacInterface 介面
ms.date: 01/16/2019
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
ms.openlocfilehash: 745ecfbffaad841e1ceb9216802644ba9dd5b94e
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416319"
---
# <a name="isosdacinterface-interface"></a><span data-ttu-id="15bd3-102">ISOSDacInterface 介面</span><span class="sxs-lookup"><span data-stu-id="15bd3-102">ISOSDacInterface Interface</span></span>

<span data-ttu-id="15bd3-103">提供 helper 方法來存取資料，從`SOS`。</span><span class="sxs-lookup"><span data-stu-id="15bd3-103">Provides helper methods to access data from `SOS`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="15bd3-104">方法</span><span class="sxs-lookup"><span data-stu-id="15bd3-104">Methods</span></span>

| <span data-ttu-id="15bd3-105">方法</span><span class="sxs-lookup"><span data-stu-id="15bd3-105">Method</span></span>                                                                                                               | <span data-ttu-id="15bd3-106">描述</span><span class="sxs-lookup"><span data-stu-id="15bd3-106">Description</span></span>                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="15bd3-107">GetMethodDescData</span><span class="sxs-lookup"><span data-stu-id="15bd3-107">GetMethodDescData</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-getmethoddescdata-method.md) | <span data-ttu-id="15bd3-108">取得的資料指定[MethodDesc](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="15bd3-108">Gets the data for the given [MethodDesc](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span></span> |

## <a name="remarks"></a><span data-ttu-id="15bd3-109">備註</span><span class="sxs-lookup"><span data-stu-id="15bd3-109">Remarks</span></span>

<span data-ttu-id="15bd3-110">此介面的執行階段內，而且不會公開透過任何標頭或程式庫檔案。</span><span class="sxs-lookup"><span data-stu-id="15bd3-110">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="15bd3-111">不過，它是 COM 介面衍生自`IUnknown`含有 GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` ，可以透過一般的 COM 機制取得。</span><span class="sxs-lookup"><span data-stu-id="15bd3-111">However, it's a COM interface that derives from `IUnknown` with GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="15bd3-112">需求</span><span class="sxs-lookup"><span data-stu-id="15bd3-112">Requirements</span></span>

<span data-ttu-id="15bd3-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="15bd3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="15bd3-114">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="15bd3-114">**Header:** None</span></span>  
<span data-ttu-id="15bd3-115">**程式庫：** 無</span><span class="sxs-lookup"><span data-stu-id="15bd3-115">**Library:** None</span></span>  
<span data-ttu-id="15bd3-116">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="15bd3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="15bd3-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15bd3-117">See Also</span></span>

- [<span data-ttu-id="15bd3-118">偵錯</span><span class="sxs-lookup"><span data-stu-id="15bd3-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="15bd3-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="15bd3-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
