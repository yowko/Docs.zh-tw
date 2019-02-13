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
ms.openlocfilehash: 1bdc958f2516bcd7c2eb74312fbf478e6d49535a
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221417"
---
# <a name="icordebugprocess4-interface"></a><span data-ttu-id="c979d-102">ICorDebugProcess4 介面</span><span class="sxs-lookup"><span data-stu-id="c979d-102">ICorDebugProcess4 Interface</span></span>

<span data-ttu-id="c979d-103">提供支援失控程序執行。</span><span class="sxs-lookup"><span data-stu-id="c979d-103">Provides support for out of process execution control.</span></span>

## <a name="methods"></a><span data-ttu-id="c979d-104">方法</span><span class="sxs-lookup"><span data-stu-id="c979d-104">Methods</span></span>

| <span data-ttu-id="c979d-105">方法</span><span class="sxs-lookup"><span data-stu-id="c979d-105">Method</span></span>                                                                 | <span data-ttu-id="c979d-106">描述</span><span class="sxs-lookup"><span data-stu-id="c979d-106">Description</span></span>                                                                                             |
| ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="c979d-107">ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="c979d-107">ProcessStateChanged</span></span>](icordebugprocess4-processstatechanged-method.md) | <span data-ttu-id="c979d-108">通知 ICorDebug 管線外的處理序偵錯工具會繼續偵錯的項目執行。</span><span class="sxs-lookup"><span data-stu-id="c979d-108">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span> |

## <a name="remarks"></a><span data-ttu-id="c979d-109">備註</span><span class="sxs-lookup"><span data-stu-id="c979d-109">Remarks</span></span>

<span data-ttu-id="c979d-110">此介面內的執行階段，而且未透過任何標頭或程式庫檔案。</span><span class="sxs-lookup"><span data-stu-id="c979d-110">This interface lives inside the runtime and isn't exposed through any headers or library files.</span></span> <span data-ttu-id="c979d-111">不過，它是 COM 介面衍生自`IUnknown`含有 GUID `E930C679-78AF-4953-8AB7-B0AABF0F9F80` ，可以透過一般的 COM 機制取得。</span><span class="sxs-lookup"><span data-stu-id="c979d-111">However, it's a COM interface that derives from `IUnknown` with GUID `E930C679-78AF-4953-8AB7-B0AABF0F9F80` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="c979d-112">需求</span><span class="sxs-lookup"><span data-stu-id="c979d-112">Requirements</span></span>

<span data-ttu-id="c979d-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c979d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="c979d-114">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="c979d-114">**Header:** None</span></span>

<span data-ttu-id="c979d-115">**程式庫：** 無</span><span class="sxs-lookup"><span data-stu-id="c979d-115">**Library:** None</span></span>

<span data-ttu-id="c979d-116">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c979d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c979d-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c979d-117">See also</span></span>

- [<span data-ttu-id="c979d-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="c979d-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c979d-119">偵錯</span><span class="sxs-lookup"><span data-stu-id="c979d-119">Debugging</span></span>](index.md)
