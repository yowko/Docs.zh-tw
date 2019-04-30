---
title: Initialize 函式 （Unmanaged API 參考）
description: Initialize 函式會執行 WMI 初始化。
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c71b2b6d6f102d19d30d480ee9bafcac3c204be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049293"
---
# <a name="initialize-function"></a><span data-ttu-id="83527-103">Initialize 函式</span><span class="sxs-lookup"><span data-stu-id="83527-103">Initialize function</span></span>

<span data-ttu-id="83527-104">執行 WMI 初始化。</span><span class="sxs-lookup"><span data-stu-id="83527-104">Performs WMI initialization.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="83527-105">語法</span><span class="sxs-lookup"><span data-stu-id="83527-105">Syntax</span></span>

```cpp
HRESULT Initialize(
   [in] boolean bAllowIManagementObjectQI
);
```

## <a name="parameters"></a><span data-ttu-id="83527-106">參數</span><span class="sxs-lookup"><span data-stu-id="83527-106">Parameters</span></span>

`bAllowIManagementObjectQI`

<span data-ttu-id="83527-107">[in]`true`來表示允許 WMI 物件上的呼叫 QueryInterface;`false`否則。</span><span class="sxs-lookup"><span data-stu-id="83527-107">[in] `true` to indicate that calls to QueryInterface on WMI objects are allowed; `false` otherwise.</span></span>

## <a name="return-value"></a><span data-ttu-id="83527-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="83527-108">Return value</span></span>

<span data-ttu-id="83527-109">此函數永遠會傳回`S_OK`(0)。</span><span class="sxs-lookup"><span data-stu-id="83527-109">The function always returns `S_OK` (0).</span></span>

## <a name="requirements"></a><span data-ttu-id="83527-110">需求</span><span class="sxs-lookup"><span data-stu-id="83527-110">Requirements</span></span>

<span data-ttu-id="83527-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="83527-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="83527-112">**標頭：** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="83527-112">**Header:** WMINet_Utils.def</span></span>

<span data-ttu-id="83527-113">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="83527-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="83527-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83527-114">See also</span></span>

- [<span data-ttu-id="83527-115">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="83527-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
