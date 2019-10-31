---
title: ICorDebugCode::GetSize 方法
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetSize method [.NET Framework debugging]
ms.assetid: 115bc6de-f5e2-4e8e-bb38-c7cf54045434
topic_type:
- apiref
ms.openlocfilehash: 2370ff5d99078ceb1ae0509e660c046dd7a1537e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125610"
---
# <a name="icordebugcodegetsize-method"></a><span data-ttu-id="c6dfb-102">ICorDebugCode::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="c6dfb-102">ICorDebugCode::GetSize Method</span></span>

<span data-ttu-id="c6dfb-103">取得這個 "ICorDebugCode" 所表示之二進位代碼的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-103">Gets the size, in bytes, of the binary code represented by this "ICorDebugCode".</span></span>

## <a name="syntax"></a><span data-ttu-id="c6dfb-104">語法</span><span class="sxs-lookup"><span data-stu-id="c6dfb-104">Syntax</span></span>

```cpp
HRESULT GetSize (
    [out] ULONG32    *pcBytes
);
```

## <a name="parameters"></a><span data-ttu-id="c6dfb-105">參數</span><span class="sxs-lookup"><span data-stu-id="c6dfb-105">Parameters</span></span>

`pcBytes`  
<span data-ttu-id="c6dfb-106">脫銷這個 `ICorDebugCode` 物件所代表之二進位代碼大小的指標（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-106">[out] A pointer to the size, in bytes, of the binary code that this `ICorDebugCode` object represents.</span></span>

## <a name="requirements"></a><span data-ttu-id="c6dfb-107">需求</span><span class="sxs-lookup"><span data-stu-id="c6dfb-107">Requirements</span></span>

<span data-ttu-id="c6dfb-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="c6dfb-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6dfb-109">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="c6dfb-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6dfb-110">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="c6dfb-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6dfb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
