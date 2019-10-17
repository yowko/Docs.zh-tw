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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25349f7c8274b818df2cd1bc5d67856e31efecc4
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395536"
---
# <a name="icordebugcodegetsize-method"></a><span data-ttu-id="3bebe-102">ICorDebugCode::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="3bebe-102">ICorDebugCode::GetSize Method</span></span>

<span data-ttu-id="3bebe-103">取得這個 "ICorDebugCode" 所表示之二進位代碼的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="3bebe-103">Gets the size, in bytes, of the binary code represented by this "ICorDebugCode".</span></span>

## <a name="syntax"></a><span data-ttu-id="3bebe-104">語法</span><span class="sxs-lookup"><span data-stu-id="3bebe-104">Syntax</span></span>

```cpp
HRESULT GetSize (
    [out] ULONG32    *pcBytes
);
```

## <a name="parameters"></a><span data-ttu-id="3bebe-105">參數</span><span class="sxs-lookup"><span data-stu-id="3bebe-105">Parameters</span></span>

`pcBytes`  
<span data-ttu-id="3bebe-106">脫銷這個 @no__t 0 物件所代表之二進位代碼大小的指標（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="3bebe-106">[out] A pointer to the size, in bytes, of the binary code that this `ICorDebugCode` object represents.</span></span>

## <a name="requirements"></a><span data-ttu-id="3bebe-107">需求</span><span class="sxs-lookup"><span data-stu-id="3bebe-107">Requirements</span></span>

<span data-ttu-id="3bebe-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3bebe-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="3bebe-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3bebe-109">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="3bebe-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3bebe-110">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="3bebe-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bebe-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
