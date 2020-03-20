---
title: ICorDebugProcess5::GetTypeFields 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeFields
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeFields
helpviewer_keywords:
- GetTypeFields method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeFields method [.NET Framework debugging]
ms.assetid: 6a0ad3ee-dacb-47e9-abae-4536bcc4804b
topic_type:
- apiref
ms.openlocfilehash: 29006eba3d3a523fd24a461207ab12222a639782
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178595"
---
# <a name="icordebugprocess5gettypefields-method"></a><span data-ttu-id="b9ec8-102">ICorDebugProcess5::GetTypeFields 方法</span><span class="sxs-lookup"><span data-stu-id="b9ec8-102">ICorDebugProcess5::GetTypeFields Method</span></span>
<span data-ttu-id="b9ec8-103">提供有關屬於類型的欄位的資訊。</span><span class="sxs-lookup"><span data-stu-id="b9ec8-103">Provides information about the fields that belong to a type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9ec8-104">語法</span><span class="sxs-lookup"><span data-stu-id="b9ec8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],
    [out] ULONG32 *pceltNeeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9ec8-105">參數</span><span class="sxs-lookup"><span data-stu-id="b9ec8-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="b9ec8-106">[在]檢索欄位資訊的類型的類型識別碼。</span><span class="sxs-lookup"><span data-stu-id="b9ec8-106">[in] The identifier of the type whose field information is retrieved.</span></span>  
  
 `celt`  
 <span data-ttu-id="b9ec8-107">[在]要檢索欄位資訊[COR_FIELD](cor-field-structure.md)物件數。</span><span class="sxs-lookup"><span data-stu-id="b9ec8-107">[in] The number of [COR_FIELD](cor-field-structure.md) objects whose field information is to be retrieved.</span></span>  
  
 `fields`  
 <span data-ttu-id="b9ec8-108">[出]COR_FIELD[物件陣列](cor-field-structure.md)，提供有關屬於該類型的欄位的資訊。</span><span class="sxs-lookup"><span data-stu-id="b9ec8-108">[out] An array of [COR_FIELD](cor-field-structure.md) objects that provide information about the fields that belong to the type.</span></span>  
  
 `pceltNeeded`  
 <span data-ttu-id="b9ec8-109">[出]指向 中包含的`fields`[COR_FIELD](cor-field-structure.md)物件的數量的指標。</span><span class="sxs-lookup"><span data-stu-id="b9ec8-109">[out] A pointer to the number of [COR_FIELD](cor-field-structure.md) objects included in `fields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9ec8-110">備註</span><span class="sxs-lookup"><span data-stu-id="b9ec8-110">Remarks</span></span>  
 <span data-ttu-id="b9ec8-111">參數`celt`指定方法用於填充`fields`的欄位資訊的欄位數應對應于`COR_TYPE_LAYOUT::numFields`欄位的值。</span><span class="sxs-lookup"><span data-stu-id="b9ec8-111">The `celt` parameter, which specifies the number of fields whose field information the method uses to populate `fields`, should correspond to the value of the `COR_TYPE_LAYOUT::numFields` field.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9ec8-112">需求</span><span class="sxs-lookup"><span data-stu-id="b9ec8-112">Requirements</span></span>  
 <span data-ttu-id="b9ec8-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b9ec8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9ec8-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9ec8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9ec8-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9ec8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9ec8-116">**.NET 框架版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9ec8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9ec8-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9ec8-117">See also</span></span>

- [<span data-ttu-id="b9ec8-118">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="b9ec8-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="b9ec8-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b9ec8-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
