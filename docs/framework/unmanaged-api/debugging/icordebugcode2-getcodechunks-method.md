---
title: ICorDebugCode2::GetCodeChunks 方法
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCodeChunks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCodeChunks
helpviewer_keywords:
- GetCodeChunks method [.NET Framework debugging]
- ICorDebugCode2::GetCodeChunks method [.NET Framework debugging]
ms.assetid: 210a2f02-2678-4555-bc4a-78a0408764c8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1bdaf6391ca5c19f073708d6258ad5775bec9824
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700734"
---
# <a name="icordebugcode2getcodechunks-method"></a><span data-ttu-id="76088-102">ICorDebugCode2::GetCodeChunks 方法</span><span class="sxs-lookup"><span data-stu-id="76088-102">ICorDebugCode2::GetCodeChunks Method</span></span>

<span data-ttu-id="76088-103">取得此程式碼物件所組成的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="76088-103">Gets the chunks of code that this code object is composed of.</span></span>

## <a name="syntax"></a><span data-ttu-id="76088-104">語法</span><span class="sxs-lookup"><span data-stu-id="76088-104">Syntax</span></span>

```cpp
HRESULT GetCodeChunks (
    [in]  ULONG32     cbufSize,
    [out] ULONG32     *pcnumChunks,
    [out, size_is(cbufSize), length_is(*pcnumChunks)]
        CodeChunkInfo chunks[]
);
```

## <a name="parameters"></a><span data-ttu-id="76088-105">參數</span><span class="sxs-lookup"><span data-stu-id="76088-105">Parameters</span></span>

 `cbufSize`  
 <span data-ttu-id="76088-106">在@No__t-0 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="76088-106">[in] Size of the `chunks` array.</span></span>

 `pcnumChunks`  
 <span data-ttu-id="76088-107">脫銷@No__t-0 陣列中傳回的區塊數目。</span><span class="sxs-lookup"><span data-stu-id="76088-107">[out] The number of chunks returned in the `chunks` array.</span></span>

 `chunks`  
 <span data-ttu-id="76088-108">脫銷"CodeChunkInfo" 結構的陣列，其中每一個都代表一個程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="76088-108">[out] An array of "CodeChunkInfo" structures, each of which represents a single chunk of code.</span></span> <span data-ttu-id="76088-109">如果 `cbufSize` 的值為0，則這個參數可以是 null。</span><span class="sxs-lookup"><span data-stu-id="76088-109">If the value of `cbufSize` is 0, this parameter can be null.</span></span>

## <a name="remarks"></a><span data-ttu-id="76088-110">備註</span><span class="sxs-lookup"><span data-stu-id="76088-110">Remarks</span></span>

 <span data-ttu-id="76088-111">程式碼區塊永遠不會重迭，而且它們會遵循[ICorDebugCode：： GetCode](icordebugcode-getcode-method.md)串連的順序。</span><span class="sxs-lookup"><span data-stu-id="76088-111">The code chunks will never overlap, and they will follow the order in which they would have been concatenated by [ICorDebugCode::GetCode](icordebugcode-getcode-method.md).</span></span> <span data-ttu-id="76088-112">.NET Framework 版本2.0 中的 Microsoft 中繼語言（MSIL）程式碼物件將會包含單一程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="76088-112">A Microsoft intermediate language (MSIL) code object in the .NET Framework version 2.0 will comprise a single code chunk.</span></span>

## <a name="requirements"></a><span data-ttu-id="76088-113">需求</span><span class="sxs-lookup"><span data-stu-id="76088-113">Requirements</span></span>

 <span data-ttu-id="76088-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="76088-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="76088-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="76088-115">**Header:** CorDebug.idl, CorDebug.h</span></span>

 <span data-ttu-id="76088-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76088-116">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="76088-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76088-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
 
