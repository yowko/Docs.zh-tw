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
ms.openlocfilehash: 12d4e63480f03bfad613f30362ddaeaf12b57a88
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791055"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a><span data-ttu-id="8b4a4-102">ICorDebugVariableHome：： GetArgumentIndex 方法</span><span class="sxs-lookup"><span data-stu-id="8b4a4-102">ICorDebugVariableHome::GetArgumentIndex Method</span></span>

<span data-ttu-id="8b4a4-103">取得函數引數的索引。</span><span class="sxs-lookup"><span data-stu-id="8b4a4-103">Gets the index of a function argument.</span></span>

## <a name="syntax"></a><span data-ttu-id="8b4a4-104">語法</span><span class="sxs-lookup"><span data-stu-id="8b4a4-104">Syntax</span></span>

```cpp
HRESULT GetArgumentIndex(
    [out] ULONG32* pArgumentIndex
);
```

## <a name="parameters"></a><span data-ttu-id="8b4a4-105">參數</span><span class="sxs-lookup"><span data-stu-id="8b4a4-105">Parameters</span></span>

`pArgumentIndex`\
<span data-ttu-id="8b4a4-106">脫銷引數索引的指標。</span><span class="sxs-lookup"><span data-stu-id="8b4a4-106">[out] A pointer to the argument index.</span></span>

## <a name="return-value"></a><span data-ttu-id="8b4a4-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="8b4a4-107">Return Value</span></span>

<span data-ttu-id="8b4a4-108">方法會傳回下列值。</span><span class="sxs-lookup"><span data-stu-id="8b4a4-108">The method returns the following values.</span></span>

|<span data-ttu-id="8b4a4-109">{2&gt;值&lt;2}</span><span class="sxs-lookup"><span data-stu-id="8b4a4-109">Value</span></span>|<span data-ttu-id="8b4a4-110">描述</span><span class="sxs-lookup"><span data-stu-id="8b4a4-110">Description</span></span>|
|-----------|-----------------|
|`S_OK`|<span data-ttu-id="8b4a4-111">方法呼叫傳回有效的引數索引。</span><span class="sxs-lookup"><span data-stu-id="8b4a4-111">The method call returned a valid argument index.</span></span>|
|`E_FAIL`|<span data-ttu-id="8b4a4-112">目前的[ICorDebugVariableHome](icordebugvariablehome-interface.md)實例代表本機變數。</span><span class="sxs-lookup"><span data-stu-id="8b4a4-112">The current [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance represents a local variable.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8b4a4-113">備註</span><span class="sxs-lookup"><span data-stu-id="8b4a4-113">Remarks</span></span>

<span data-ttu-id="8b4a4-114">引數索引可以用來抓取此引數的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="8b4a4-114">The argument index can be used to retrieve metadata for this argument.</span></span>

## <a name="requirements"></a><span data-ttu-id="8b4a4-115">需求</span><span class="sxs-lookup"><span data-stu-id="8b4a4-115">Requirements</span></span>

<span data-ttu-id="8b4a4-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8b4a4-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="8b4a4-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b4a4-117">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="8b4a4-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b4a4-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="8b4a4-119">**.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b4a4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="8b4a4-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="8b4a4-120">See also</span></span>

- [<span data-ttu-id="8b4a4-121">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="8b4a4-121">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
