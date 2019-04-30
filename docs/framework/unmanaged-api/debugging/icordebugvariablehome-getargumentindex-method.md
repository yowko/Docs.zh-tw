---
title: ICorDebugVariableHome::GetArgumentIndex 方法
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2457dff3063e47f1fb9d040caac1bc08441e1739
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986787"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a><span data-ttu-id="c38b5-102">ICorDebugVariableHome::GetArgumentIndex 方法</span><span class="sxs-lookup"><span data-stu-id="c38b5-102">ICorDebugVariableHome::GetArgumentIndex Method</span></span>

<span data-ttu-id="c38b5-103">取得函式引數的索引。</span><span class="sxs-lookup"><span data-stu-id="c38b5-103">Gets the index of a function argument.</span></span>

## <a name="syntax"></a><span data-ttu-id="c38b5-104">語法</span><span class="sxs-lookup"><span data-stu-id="c38b5-104">Syntax</span></span>

```cpp
HRESULT GetArgumentIndex(
    [out] ULONG32* pArgumentIndex
);
```

## <a name="parameters"></a><span data-ttu-id="c38b5-105">參數</span><span class="sxs-lookup"><span data-stu-id="c38b5-105">Parameters</span></span>

`pArgumentIndex`\
<span data-ttu-id="c38b5-106">[out]引數索引指標。</span><span class="sxs-lookup"><span data-stu-id="c38b5-106">[out] A pointer to the argument index.</span></span>

## <a name="return-value"></a><span data-ttu-id="c38b5-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="c38b5-107">Return Value</span></span>

<span data-ttu-id="c38b5-108">方法會傳回下列值。</span><span class="sxs-lookup"><span data-stu-id="c38b5-108">The method returns the following values.</span></span>

|<span data-ttu-id="c38b5-109">值</span><span class="sxs-lookup"><span data-stu-id="c38b5-109">Value</span></span>|<span data-ttu-id="c38b5-110">描述</span><span class="sxs-lookup"><span data-stu-id="c38b5-110">Description</span></span>|
|-----------|-----------------|
|`S_OK`|<span data-ttu-id="c38b5-111">方法呼叫傳回的有效引數索引。</span><span class="sxs-lookup"><span data-stu-id="c38b5-111">The method call returned a valid argument index.</span></span>|
|`E_FAIL`|<span data-ttu-id="c38b5-112">目前[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)執行個體代表的本機變數。</span><span class="sxs-lookup"><span data-stu-id="c38b5-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a local variable.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c38b5-113">備註</span><span class="sxs-lookup"><span data-stu-id="c38b5-113">Remarks</span></span>

<span data-ttu-id="c38b5-114">引數索引可用來擷取中繼資料，這個引數。</span><span class="sxs-lookup"><span data-stu-id="c38b5-114">The argument index can be used to retrieve metadata for this argument.</span></span>

## <a name="requirements"></a><span data-ttu-id="c38b5-115">需求</span><span class="sxs-lookup"><span data-stu-id="c38b5-115">Requirements</span></span>

<span data-ttu-id="c38b5-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c38b5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="c38b5-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c38b5-117">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="c38b5-118">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c38b5-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="c38b5-119">**.NET framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c38b5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c38b5-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c38b5-120">See also</span></span>

- [<span data-ttu-id="c38b5-121">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="c38b5-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
