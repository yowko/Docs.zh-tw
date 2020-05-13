---
title: ICorDebugProcess4 介面
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4
helpviewer_keywords:
- ICorDebugProcess4 interface [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: fcf725ea98fa4351e72cf592f92968ee2233ecb0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213578"
---
# <a name="icordebugprocess4-interface"></a><span data-ttu-id="9cd5e-102">ICorDebugProcess4 介面</span><span class="sxs-lookup"><span data-stu-id="9cd5e-102">ICorDebugProcess4 Interface</span></span>

<span data-ttu-id="9cd5e-103">提供進程外執行控制的支援。</span><span class="sxs-lookup"><span data-stu-id="9cd5e-103">Provides support for out of process execution control.</span></span>

## <a name="methods"></a><span data-ttu-id="9cd5e-104">方法</span><span class="sxs-lookup"><span data-stu-id="9cd5e-104">Methods</span></span>

| <span data-ttu-id="9cd5e-105">方法</span><span class="sxs-lookup"><span data-stu-id="9cd5e-105">Method</span></span>                                                                 | <span data-ttu-id="9cd5e-106">描述</span><span class="sxs-lookup"><span data-stu-id="9cd5e-106">Description</span></span>                                                                                             |
| ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="9cd5e-107">ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="9cd5e-107">ProcessStateChanged</span></span>](icordebugprocess4-processstatechanged-method.md) | <span data-ttu-id="9cd5e-108">通知 ICorDebug 管線，進程外偵錯工具正在繼續偵錯專案的執行。</span><span class="sxs-lookup"><span data-stu-id="9cd5e-108">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span> |

## <a name="remarks"></a><span data-ttu-id="9cd5e-109">備註</span><span class="sxs-lookup"><span data-stu-id="9cd5e-109">Remarks</span></span>

<span data-ttu-id="9cd5e-110">這個介面存在於執行時間內，不會透過任何標頭或程式庫檔案公開。</span><span class="sxs-lookup"><span data-stu-id="9cd5e-110">This interface lives inside the runtime and isn't exposed through any headers or library files.</span></span> <span data-ttu-id="9cd5e-111">不過，它是衍生自的 COM 介面，其 `IUnknown` 具有 `E930C679-78AF-4953-8AB7-B0AABF0F9F80` 可透過一般 COM 機制取得的 GUID。</span><span class="sxs-lookup"><span data-stu-id="9cd5e-111">However, it's a COM interface that derives from `IUnknown` with GUID `E930C679-78AF-4953-8AB7-B0AABF0F9F80` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="9cd5e-112">需求</span><span class="sxs-lookup"><span data-stu-id="9cd5e-112">Requirements</span></span>

<span data-ttu-id="9cd5e-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9cd5e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="9cd5e-114">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="9cd5e-114">**Header:** None</span></span>

<span data-ttu-id="9cd5e-115">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="9cd5e-115">**Library:** None</span></span>

<span data-ttu-id="9cd5e-116">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cd5e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="9cd5e-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="9cd5e-117">See also</span></span>

- [<span data-ttu-id="9cd5e-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="9cd5e-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="9cd5e-119">偵錯</span><span class="sxs-lookup"><span data-stu-id="9cd5e-119">Debugging</span></span>](index.md)
