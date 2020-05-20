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
ms.openlocfilehash: c9b4e6e5b36fe38b6c0ea78f6d1848d155008bcc
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420964"
---
# <a name="isosdacinterface-interface"></a><span data-ttu-id="640d6-102">ISOSDacInterface 介面</span><span class="sxs-lookup"><span data-stu-id="640d6-102">ISOSDacInterface Interface</span></span>

<span data-ttu-id="640d6-103">提供 helper 方法，以存取來自的資料 `SOS` 。</span><span class="sxs-lookup"><span data-stu-id="640d6-103">Provides helper methods to access data from `SOS`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="640d6-104">方法</span><span class="sxs-lookup"><span data-stu-id="640d6-104">Methods</span></span>

| <span data-ttu-id="640d6-105">方法</span><span class="sxs-lookup"><span data-stu-id="640d6-105">Method</span></span>                                                                                                               | <span data-ttu-id="640d6-106">描述</span><span class="sxs-lookup"><span data-stu-id="640d6-106">Description</span></span>                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="640d6-107">GetMethodDescData</span><span class="sxs-lookup"><span data-stu-id="640d6-107">GetMethodDescData</span></span>](isosdacinterface-getmethoddescdata-method.md) | <span data-ttu-id="640d6-108">取得給定 MethodDesc 指標的資料。</span><span class="sxs-lookup"><span data-stu-id="640d6-108">Gets the data for the given MethodDesc pointer.</span></span> |
| [<span data-ttu-id="640d6-109">GetMethodDescPtrFromIP</span><span class="sxs-lookup"><span data-stu-id="640d6-109">GetMethodDescPtrFromIP</span></span>](isosdacinterface-getmethoddescptrfromip-method.md) | <span data-ttu-id="640d6-110">抓取 MethodDesc 的指標，其對應的方法包含指定的原生指令位址。</span><span class="sxs-lookup"><span data-stu-id="640d6-110">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span> |
| [<span data-ttu-id="640d6-111">GetModuleData</span><span class="sxs-lookup"><span data-stu-id="640d6-111">GetModuleData</span></span>](isosdacinterface-getmoduledata-method.md)| <span data-ttu-id="640d6-112">提取對應至在指定位址載入之模組的資料。</span><span class="sxs-lookup"><span data-stu-id="640d6-112">Fetches the data corresponding to the module loaded at a given address.</span></span> |

## <a name="remarks"></a><span data-ttu-id="640d6-113">備註</span><span class="sxs-lookup"><span data-stu-id="640d6-113">Remarks</span></span>

<span data-ttu-id="640d6-114">這個介面存在於執行時間內，而且不會透過任何標頭或程式庫檔案公開。</span><span class="sxs-lookup"><span data-stu-id="640d6-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="640d6-115">不過，它是衍生自的 COM 介面，其 `IUnknown` 具有 `436f00f2-b42a-4b9f-870c-e73db66ae930` 可透過一般 COM 機制取得的 GUID。</span><span class="sxs-lookup"><span data-stu-id="640d6-115">However, it's a COM interface that derives from `IUnknown` with GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="640d6-116">需求</span><span class="sxs-lookup"><span data-stu-id="640d6-116">Requirements</span></span>

<span data-ttu-id="640d6-117">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="640d6-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="640d6-118">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="640d6-118">**Header:** None</span></span>  
<span data-ttu-id="640d6-119">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="640d6-119">**Library:** None</span></span>  
<span data-ttu-id="640d6-120">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="640d6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="640d6-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="640d6-121">See also</span></span>

- [<span data-ttu-id="640d6-122">偵錯</span><span class="sxs-lookup"><span data-stu-id="640d6-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="640d6-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="640d6-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
