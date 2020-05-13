---
title: ICorDebugProcess4：:P rocessStateChanged 方法
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
ms.openlocfilehash: 910c411d2c63ce2c6cf262e28e08546657dc2a4c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213565"
---
# <a name="icordebugprocess4processstatechanged-method"></a><span data-ttu-id="c7581-102">ICorDebugProcess4：:P rocessStateChanged 方法</span><span class="sxs-lookup"><span data-stu-id="c7581-102">ICorDebugProcess4::ProcessStateChanged Method</span></span>

<span data-ttu-id="c7581-103">通知 ICorDebug 管線，進程外偵錯工具正在繼續偵錯專案的執行。</span><span class="sxs-lookup"><span data-stu-id="c7581-103">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span>

## <a name="syntax"></a><span data-ttu-id="c7581-104">語法</span><span class="sxs-lookup"><span data-stu-id="c7581-104">Syntax</span></span>

```cpp
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a><span data-ttu-id="c7581-105">參數</span><span class="sxs-lookup"><span data-stu-id="c7581-105">Parameters</span></span>

 `eChange`\
<span data-ttu-id="c7581-106">在[CorDebugStateChange 列舉](cordebugstatechange-enumeration.md)的成員，描述進程的執行狀態變更。</span><span class="sxs-lookup"><span data-stu-id="c7581-106">[in] A member of the [CorDebugStateChange enumeration](cordebugstatechange-enumeration.md) describing a change in the process's execution state.</span></span>

## <a name="remarks"></a><span data-ttu-id="c7581-107">備註</span><span class="sxs-lookup"><span data-stu-id="c7581-107">Remarks</span></span>

<span data-ttu-id="c7581-108">提供的方法是介面的一部分 `ICorDebugProcess4` ，而且會對應至虛擬方法資料表的第四個插槽。</span><span class="sxs-lookup"><span data-stu-id="c7581-108">The provided method is part of the `ICorDebugProcess4` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="c7581-109">需求</span><span class="sxs-lookup"><span data-stu-id="c7581-109">Requirements</span></span>

 <span data-ttu-id="c7581-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c7581-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="c7581-111">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="c7581-111">**Header:** None</span></span>

 <span data-ttu-id="c7581-112">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="c7581-112">**Library:** None</span></span>

 <span data-ttu-id="c7581-113">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7581-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c7581-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="c7581-114">See also</span></span>

- [<span data-ttu-id="c7581-115">ICorDebugProcess4 介面</span><span class="sxs-lookup"><span data-stu-id="c7581-115">ICorDebugProcess4 Interface</span></span>](icordebugprocess4-interface.md)
- [<span data-ttu-id="c7581-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="c7581-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c7581-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="c7581-117">Debugging</span></span>](index.md)
