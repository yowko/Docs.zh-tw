---
title: ICorDebugProcess4：:Process狀態更改方法
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4::ProcessStateChanged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4::ProcessStateChanged
helpviewer_keywords:
- ICorDebugProcess4::ProcessStateChanged method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: a6f36f5b86b4fa58ce2a4ef4aa23d527f797a5a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178634"
---
# <a name="icordebugprocess4processstatechanged-method"></a><span data-ttu-id="a6e43-102">ICorDebugProcess4：:Process狀態更改方法</span><span class="sxs-lookup"><span data-stu-id="a6e43-102">ICorDebugProcess4::ProcessStateChanged Method</span></span>

<span data-ttu-id="a6e43-103">通知 ICorDebug 管道進程外調試器正在繼續執行調試器。</span><span class="sxs-lookup"><span data-stu-id="a6e43-103">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span>

## <a name="syntax"></a><span data-ttu-id="a6e43-104">語法</span><span class="sxs-lookup"><span data-stu-id="a6e43-104">Syntax</span></span>

```cpp
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a><span data-ttu-id="a6e43-105">參數</span><span class="sxs-lookup"><span data-stu-id="a6e43-105">Parameters</span></span>

 `eChange`\
<span data-ttu-id="a6e43-106">[在][CorDebugStateChange 計數](cordebugstatechange-enumeration.md)的成員，描述進程執行狀態的變化。</span><span class="sxs-lookup"><span data-stu-id="a6e43-106">[in] A member of the [CorDebugStateChange enumeration](cordebugstatechange-enumeration.md) describing a change in the process's execution state.</span></span>

## <a name="remarks"></a><span data-ttu-id="a6e43-107">備註</span><span class="sxs-lookup"><span data-stu-id="a6e43-107">Remarks</span></span>

<span data-ttu-id="a6e43-108">提供的方法是介面的一`ICorDebugProcess4`部分，對應于虛擬方法表的第四個槽。</span><span class="sxs-lookup"><span data-stu-id="a6e43-108">The provided method is part of the `ICorDebugProcess4` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="a6e43-109">需求</span><span class="sxs-lookup"><span data-stu-id="a6e43-109">Requirements</span></span>

 <span data-ttu-id="a6e43-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a6e43-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="a6e43-111">**標題：** 沒有</span><span class="sxs-lookup"><span data-stu-id="a6e43-111">**Header:** None</span></span>

 <span data-ttu-id="a6e43-112">**庫：** 沒有</span><span class="sxs-lookup"><span data-stu-id="a6e43-112">**Library:** None</span></span>

 <span data-ttu-id="a6e43-113">**.NET 框架版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6e43-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a6e43-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6e43-114">See also</span></span>

- [<span data-ttu-id="a6e43-115">ICorDebugProcess4 介面</span><span class="sxs-lookup"><span data-stu-id="a6e43-115">ICorDebugProcess4 Interface</span></span>](icordebugprocess4-interface.md)
- [<span data-ttu-id="a6e43-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a6e43-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a6e43-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="a6e43-117">Debugging</span></span>](index.md)
