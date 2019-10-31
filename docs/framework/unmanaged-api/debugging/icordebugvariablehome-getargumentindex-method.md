---
title: ICorDebugVariableHome：： GetArgumentIndex 方法
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetArgumentIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetArgumentIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetArgumentIndex method [.NET Framework debugging]
- GetArgumentIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: e86fcc72-388d-4009-ab21-8f9c3323e9a3
topic_type:
- apiref
ms.openlocfilehash: 86b2815c6f95c674c49bba7455e8497192bd8bac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125145"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a><span data-ttu-id="89d68-102">ICorDebugVariableHome：： GetArgumentIndex 方法</span><span class="sxs-lookup"><span data-stu-id="89d68-102">ICorDebugVariableHome::GetArgumentIndex Method</span></span>

<span data-ttu-id="89d68-103">取得函數引數的索引。</span><span class="sxs-lookup"><span data-stu-id="89d68-103">Gets the index of a function argument.</span></span>

## <a name="syntax"></a><span data-ttu-id="89d68-104">語法</span><span class="sxs-lookup"><span data-stu-id="89d68-104">Syntax</span></span>

```cpp
HRESULT GetArgumentIndex(
    [out] ULONG32* pArgumentIndex
);
```

## <a name="parameters"></a><span data-ttu-id="89d68-105">參數</span><span class="sxs-lookup"><span data-stu-id="89d68-105">Parameters</span></span>

`pArgumentIndex`\
<span data-ttu-id="89d68-106">脫銷引數索引的指標。</span><span class="sxs-lookup"><span data-stu-id="89d68-106">[out] A pointer to the argument index.</span></span>

## <a name="return-value"></a><span data-ttu-id="89d68-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="89d68-107">Return Value</span></span>

<span data-ttu-id="89d68-108">方法會傳回下列值。</span><span class="sxs-lookup"><span data-stu-id="89d68-108">The method returns the following values.</span></span>

|<span data-ttu-id="89d68-109">值</span><span class="sxs-lookup"><span data-stu-id="89d68-109">Value</span></span>|<span data-ttu-id="89d68-110">描述</span><span class="sxs-lookup"><span data-stu-id="89d68-110">Description</span></span>|
|-----------|-----------------|
|`S_OK`|<span data-ttu-id="89d68-111">方法呼叫傳回有效的引數索引。</span><span class="sxs-lookup"><span data-stu-id="89d68-111">The method call returned a valid argument index.</span></span>|
|`E_FAIL`|<span data-ttu-id="89d68-112">目前的[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)實例代表本機變數。</span><span class="sxs-lookup"><span data-stu-id="89d68-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a local variable.</span></span>|

## <a name="remarks"></a><span data-ttu-id="89d68-113">備註</span><span class="sxs-lookup"><span data-stu-id="89d68-113">Remarks</span></span>

<span data-ttu-id="89d68-114">引數索引可以用來抓取此引數的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="89d68-114">The argument index can be used to retrieve metadata for this argument.</span></span>

## <a name="requirements"></a><span data-ttu-id="89d68-115">需求</span><span class="sxs-lookup"><span data-stu-id="89d68-115">Requirements</span></span>

<span data-ttu-id="89d68-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="89d68-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="89d68-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="89d68-117">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="89d68-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89d68-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="89d68-119">**.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89d68-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="89d68-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="89d68-120">See also</span></span>

- [<span data-ttu-id="89d68-121">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="89d68-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
