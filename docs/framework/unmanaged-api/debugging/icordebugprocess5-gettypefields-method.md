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
ms.openlocfilehash: e4eba37487ca2ee0a88caf5a59f86949a6521e40
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95670936"
---
# <a name="icordebugprocess5gettypefields-method"></a><span data-ttu-id="446cd-102">ICorDebugProcess5::GetTypeFields 方法</span><span class="sxs-lookup"><span data-stu-id="446cd-102">ICorDebugProcess5::GetTypeFields Method</span></span>

<span data-ttu-id="446cd-103">提供屬於某類型之欄位的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="446cd-103">Provides information about the fields that belong to a type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="446cd-104">語法</span><span class="sxs-lookup"><span data-stu-id="446cd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],
    [out] ULONG32 *pceltNeeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="446cd-105">參數</span><span class="sxs-lookup"><span data-stu-id="446cd-105">Parameters</span></span>  

 `id`  
 <span data-ttu-id="446cd-106">在要抓取其欄位資訊之類型的識別碼。</span><span class="sxs-lookup"><span data-stu-id="446cd-106">[in] The identifier of the type whose field information is retrieved.</span></span>  
  
 `celt`  
 <span data-ttu-id="446cd-107">在要取出其欄位資訊的 [COR_FIELD](cor-field-structure.md) 物件數目。</span><span class="sxs-lookup"><span data-stu-id="446cd-107">[in] The number of [COR_FIELD](cor-field-structure.md) objects whose field information is to be retrieved.</span></span>  
  
 `fields`  
 <span data-ttu-id="446cd-108">擴展 [COR_FIELD](cor-field-structure.md) 物件的陣列，提供屬於此類型之欄位的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="446cd-108">[out] An array of [COR_FIELD](cor-field-structure.md) objects that provide information about the fields that belong to the type.</span></span>  
  
 `pceltNeeded`  
 <span data-ttu-id="446cd-109">擴展包含在中之 [COR_FIELD](cor-field-structure.md) 物件數目的指標 `fields` 。</span><span class="sxs-lookup"><span data-stu-id="446cd-109">[out] A pointer to the number of [COR_FIELD](cor-field-structure.md) objects included in `fields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="446cd-110">備註</span><span class="sxs-lookup"><span data-stu-id="446cd-110">Remarks</span></span>  

 <span data-ttu-id="446cd-111">`celt`參數，指定方法用來填入其欄位資訊的欄位數目 `fields` ，應該對應到欄位的值 `COR_TYPE_LAYOUT::numFields` 。</span><span class="sxs-lookup"><span data-stu-id="446cd-111">The `celt` parameter, which specifies the number of fields whose field information the method uses to populate `fields`, should correspond to the value of the `COR_TYPE_LAYOUT::numFields` field.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="446cd-112">需求</span><span class="sxs-lookup"><span data-stu-id="446cd-112">Requirements</span></span>  

 <span data-ttu-id="446cd-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="446cd-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="446cd-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="446cd-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="446cd-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="446cd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="446cd-116">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="446cd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="446cd-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="446cd-117">See also</span></span>

- [<span data-ttu-id="446cd-118">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="446cd-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="446cd-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="446cd-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
