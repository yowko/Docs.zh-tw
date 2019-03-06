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
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366825"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a><span data-ttu-id="593f2-102">ICorDebugVariableHome::GetArgumentIndex 方法</span><span class="sxs-lookup"><span data-stu-id="593f2-102">ICorDebugVariableHome::GetArgumentIndex Method</span></span>

<span data-ttu-id="593f2-103">取得函式引數的索引。</span><span class="sxs-lookup"><span data-stu-id="593f2-103">Gets the index of a function argument.</span></span>

## <a name="syntax"></a><span data-ttu-id="593f2-104">語法</span><span class="sxs-lookup"><span data-stu-id="593f2-104">Syntax</span></span>

```cpp
HRESULT GetArgumentIndex(
    [out] ULONG32* pArgumentIndex
);
```

## <a name="parameters"></a><span data-ttu-id="593f2-105">參數</span><span class="sxs-lookup"><span data-stu-id="593f2-105">Parameters</span></span>

`pArgumentIndex`\
<span data-ttu-id="593f2-106">[out]引數索引指標。</span><span class="sxs-lookup"><span data-stu-id="593f2-106">[out] A pointer to the argument index.</span></span>

## <a name="return-value"></a><span data-ttu-id="593f2-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="593f2-107">Return Value</span></span>

<span data-ttu-id="593f2-108">方法會傳回下列值。</span><span class="sxs-lookup"><span data-stu-id="593f2-108">The method returns the following values.</span></span>

|<span data-ttu-id="593f2-109">值</span><span class="sxs-lookup"><span data-stu-id="593f2-109">Value</span></span>|<span data-ttu-id="593f2-110">描述</span><span class="sxs-lookup"><span data-stu-id="593f2-110">Description</span></span>|
|-----------|-----------------|
|`S_OK`|<span data-ttu-id="593f2-111">方法呼叫傳回的有效引數索引。</span><span class="sxs-lookup"><span data-stu-id="593f2-111">The method call returned a valid argument index.</span></span>|
|`E_FAIL`|<span data-ttu-id="593f2-112">目前[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)執行個體代表的本機變數。</span><span class="sxs-lookup"><span data-stu-id="593f2-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a local variable.</span></span>|

## <a name="remarks"></a><span data-ttu-id="593f2-113">備註</span><span class="sxs-lookup"><span data-stu-id="593f2-113">Remarks</span></span>

<span data-ttu-id="593f2-114">引數索引可用來擷取中繼資料，這個引數。</span><span class="sxs-lookup"><span data-stu-id="593f2-114">The argument index can be used to retrieve metadata for this argument.</span></span>

## <a name="requirements"></a><span data-ttu-id="593f2-115">需求</span><span class="sxs-lookup"><span data-stu-id="593f2-115">Requirements</span></span>

<span data-ttu-id="593f2-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="593f2-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="593f2-117">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="593f2-117">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="593f2-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="593f2-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="593f2-119">**.NET framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="593f2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="593f2-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="593f2-120">See also</span></span>

- [<span data-ttu-id="593f2-121">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="593f2-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
