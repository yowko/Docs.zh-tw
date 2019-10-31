---
title: ICorDebugModule2::ResolveAssembly 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ResolveAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ResolveAssembly
helpviewer_keywords:
- ICorDebugModule2::ResolveAssembly method [.NET Framework debugging]
- ResolveAssembly method [.NET Framework debugging]
ms.assetid: ddf9085c-7161-44bd-9609-cd2732b9009f
topic_type:
- apiref
ms.openlocfilehash: 0809a149a5a5a5e9adea059140d7b4b456337ef3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125310"
---
# <a name="icordebugmodule2resolveassembly-method"></a><span data-ttu-id="f4a8c-102">ICorDebugModule2::ResolveAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="f4a8c-102">ICorDebugModule2::ResolveAssembly Method</span></span>

<span data-ttu-id="f4a8c-103">解析指定的元資料標記所參考的元件。</span><span class="sxs-lookup"><span data-stu-id="f4a8c-103">Resolves the assembly referenced by the specified metadata token.</span></span>

## <a name="syntax"></a><span data-ttu-id="f4a8c-104">語法</span><span class="sxs-lookup"><span data-stu-id="f4a8c-104">Syntax</span></span>

```cpp
HRESULT ResolveAssembly (
    [in]  mdToken             tkAssemblyRef,
    [out] ICorDebugAssembly   **ppAssembly
);
```

## <a name="parameters"></a><span data-ttu-id="f4a8c-105">參數</span><span class="sxs-lookup"><span data-stu-id="f4a8c-105">Parameters</span></span>

`tkAssemblyRef`\
<span data-ttu-id="f4a8c-106">在參考元件的 `mdToken` 值。</span><span class="sxs-lookup"><span data-stu-id="f4a8c-106">[in] An `mdToken` value that references the assembly.</span></span>

`ppAssembly`\
<span data-ttu-id="f4a8c-107">脫銷表示元件之 ICorDebugAssembly 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="f4a8c-107">[out] A pointer to the address of an ICorDebugAssembly object that represents the assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="f4a8c-108">備註</span><span class="sxs-lookup"><span data-stu-id="f4a8c-108">Remarks</span></span>

<span data-ttu-id="f4a8c-109">如果在呼叫 `ResolveAssembly` 時尚未載入元件，則會傳回 CORDBG_E_CANNOT_RESOLVE_ASSEMBLY 的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="f4a8c-109">If the assembly is not already loaded when `ResolveAssembly` is called, an HRESULT value of CORDBG_E_CANNOT_RESOLVE_ASSEMBLY is returned.</span></span>

## <a name="requirements"></a><span data-ttu-id="f4a8c-110">需求</span><span class="sxs-lookup"><span data-stu-id="f4a8c-110">Requirements</span></span>

<span data-ttu-id="f4a8c-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f4a8c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="f4a8c-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f4a8c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="f4a8c-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4a8c-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="f4a8c-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4a8c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
