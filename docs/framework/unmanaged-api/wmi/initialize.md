---
title: Initialize 函式（非受控 API 參考）
description: Initialize 函數會執行 WMI 初始化。
ms.date: 11/06/2017
api_name:
- Initialize
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Initialize
helpviewer_keywords:
- Initialize function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: b1f96b6285911b12d72ac136127d736b75d44023
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127384"
---
# <a name="initialize-function"></a><span data-ttu-id="a7d96-103">Initialize 函式</span><span class="sxs-lookup"><span data-stu-id="a7d96-103">Initialize function</span></span>

<span data-ttu-id="a7d96-104">執行 WMI 初始化。</span><span class="sxs-lookup"><span data-stu-id="a7d96-104">Performs WMI initialization.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="a7d96-105">語法</span><span class="sxs-lookup"><span data-stu-id="a7d96-105">Syntax</span></span>

```cpp
HRESULT Initialize(
   [in] boolean bAllowIManagementObjectQI
);
```

## <a name="parameters"></a><span data-ttu-id="a7d96-106">參數</span><span class="sxs-lookup"><span data-stu-id="a7d96-106">Parameters</span></span>

`bAllowIManagementObjectQI`

<span data-ttu-id="a7d96-107">[in] `true`，表示允許對 WMI 物件上的 QueryInterface 進行呼叫;否則 `false`。</span><span class="sxs-lookup"><span data-stu-id="a7d96-107">[in] `true` to indicate that calls to QueryInterface on WMI objects are allowed; `false` otherwise.</span></span>

## <a name="return-value"></a><span data-ttu-id="a7d96-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="a7d96-108">Return value</span></span>

<span data-ttu-id="a7d96-109">函數一律會傳回 `S_OK` （0）。</span><span class="sxs-lookup"><span data-stu-id="a7d96-109">The function always returns `S_OK` (0).</span></span>

## <a name="requirements"></a><span data-ttu-id="a7d96-110">需求</span><span class="sxs-lookup"><span data-stu-id="a7d96-110">Requirements</span></span>

<span data-ttu-id="a7d96-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a7d96-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="a7d96-112">**標頭：** WMINet_Utils .def</span><span class="sxs-lookup"><span data-stu-id="a7d96-112">**Header:** WMINet_Utils.def</span></span>

<span data-ttu-id="a7d96-113">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a7d96-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a7d96-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="a7d96-114">See also</span></span>

- [<span data-ttu-id="a7d96-115">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="a7d96-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
