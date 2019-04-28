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
ms.openlocfilehash: ccaf479fc4fb90007b4999e95ee03bdd0529321e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61922144"
---
# <a name="isosdacinterface-interface"></a><span data-ttu-id="71b31-102">ISOSDacInterface 介面</span><span class="sxs-lookup"><span data-stu-id="71b31-102">ISOSDacInterface Interface</span></span>

<span data-ttu-id="71b31-103">提供 helper 方法來存取資料，從`SOS`。</span><span class="sxs-lookup"><span data-stu-id="71b31-103">Provides helper methods to access data from `SOS`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="71b31-104">方法</span><span class="sxs-lookup"><span data-stu-id="71b31-104">Methods</span></span>

| <span data-ttu-id="71b31-105">方法</span><span class="sxs-lookup"><span data-stu-id="71b31-105">Method</span></span>                                                                                                               | <span data-ttu-id="71b31-106">描述</span><span class="sxs-lookup"><span data-stu-id="71b31-106">Description</span></span>                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="71b31-107">GetMethodDescData</span><span class="sxs-lookup"><span data-stu-id="71b31-107">GetMethodDescData</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-getmethoddescdata-method.md) | <span data-ttu-id="71b31-108">取得指定 MethodDesc 指標的資料。</span><span class="sxs-lookup"><span data-stu-id="71b31-108">Gets the data for the given MethodDesc pointer.</span></span> |
| [<span data-ttu-id="71b31-109">GetMethodDescPtrFromIP</span><span class="sxs-lookup"><span data-stu-id="71b31-109">GetMethodDescPtrFromIP</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-getmethoddescptrfromip-method.md) | <span data-ttu-id="71b31-110">擷取 MethodDesc 對應包含指定的原生指令位址之方法的指標。</span><span class="sxs-lookup"><span data-stu-id="71b31-110">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span> |
| [<span data-ttu-id="71b31-111">GetModuleData</span><span class="sxs-lookup"><span data-stu-id="71b31-111">GetModuleData</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-getmoduledata-method.md)| <span data-ttu-id="71b31-112">擷取對應至指定的位址在載入模組的資料。</span><span class="sxs-lookup"><span data-stu-id="71b31-112">Fetches the data corresponding to the module loaded at a given address.</span></span> |

## <a name="remarks"></a><span data-ttu-id="71b31-113">備註</span><span class="sxs-lookup"><span data-stu-id="71b31-113">Remarks</span></span>

<span data-ttu-id="71b31-114">此介面的執行階段內，而且不會公開透過任何標頭或程式庫檔案。</span><span class="sxs-lookup"><span data-stu-id="71b31-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="71b31-115">不過，它是 COM 介面衍生自`IUnknown`含有 GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` ，可以透過一般的 COM 機制取得。</span><span class="sxs-lookup"><span data-stu-id="71b31-115">However, it's a COM interface that derives from `IUnknown` with GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="71b31-116">需求</span><span class="sxs-lookup"><span data-stu-id="71b31-116">Requirements</span></span>

<span data-ttu-id="71b31-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="71b31-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="71b31-118">**標頭：** None</span><span class="sxs-lookup"><span data-stu-id="71b31-118">**Header:** None</span></span>  
<span data-ttu-id="71b31-119">**LIBRARY:** None</span><span class="sxs-lookup"><span data-stu-id="71b31-119">**Library:** None</span></span>  
<span data-ttu-id="71b31-120">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="71b31-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="71b31-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71b31-121">See also</span></span>

- [<span data-ttu-id="71b31-122">偵錯</span><span class="sxs-lookup"><span data-stu-id="71b31-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="71b31-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="71b31-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
