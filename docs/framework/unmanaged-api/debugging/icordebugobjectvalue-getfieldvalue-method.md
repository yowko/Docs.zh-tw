---
title: ICorDebugObjectValue::GetFieldValue 方法
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.GetFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::GetFieldValue
helpviewer_keywords:
- ICorDebugObjectValue::GetFieldValue method [.NET Framework debugging]
- GetFieldValue method [.NET Framework debugging]
ms.assetid: c96770b0-3e09-47bb-bd29-20353b043459
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0fc65f5b55082970a0cd59a6850aaaa6779d0821
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766402"
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a><span data-ttu-id="9dde0-102">ICorDebugObjectValue::GetFieldValue 方法</span><span class="sxs-lookup"><span data-stu-id="9dde0-102">ICorDebugObjectValue::GetFieldValue Method</span></span>
<span data-ttu-id="9dde0-103">取得這個物件值，指定類別的指定欄位的值。</span><span class="sxs-lookup"><span data-stu-id="9dde0-103">Gets the value of the specified field of the specified class for this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dde0-104">語法</span><span class="sxs-lookup"><span data-stu-id="9dde0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9dde0-105">參數</span><span class="sxs-lookup"><span data-stu-id="9dde0-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="9dde0-106">[in]表示要取得的欄位值的類別 「 ICorDebugClass"物件的指標。</span><span class="sxs-lookup"><span data-stu-id="9dde0-106">[in] A pointer to an "ICorDebugClass" object that represents the class for which to get the field value.</span></span>  
  
 `fieldDef`  
 <span data-ttu-id="9dde0-107">[in]`mdFieldDef`參考描述欄位的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="9dde0-107">[in] An `mdFieldDef` token that references the metadata describing the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="9dde0-108">[out]表示指定之欄位的值"ICorDebugValue 」 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="9dde0-108">[out] A pointer to an "ICorDebugValue" object that represents the value of the specified field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9dde0-109">備註</span><span class="sxs-lookup"><span data-stu-id="9dde0-109">Remarks</span></span>  
 <span data-ttu-id="9dde0-110">中指定的類別`pClass`參數，必須是階層中的物件值的類別，且此欄位必須是該類別的欄位。</span><span class="sxs-lookup"><span data-stu-id="9dde0-110">The class, specified in the `pClass` parameter, must be in the hierarchy of the object value's class, and the field must be a field of that class.</span></span>  
  
 <span data-ttu-id="9dde0-111">`GetFieldValue`方法仍然會成功的泛型物件的泛型類別。</span><span class="sxs-lookup"><span data-stu-id="9dde0-111">The `GetFieldValue` method will still succeed for generic objects and generic classes.</span></span> <span data-ttu-id="9dde0-112">比方說，如果 MyDictionary\<V > 繼承自字典\<字串，V >，而且物件值的類型 MyDictionary\<int32 >，並傳遞`ICorDebugClass`字典的物件\<K，V > 將已成功取得欄位的字典\<string，int32 >。</span><span class="sxs-lookup"><span data-stu-id="9dde0-112">For example, if MyDictionary\<V> inherits from Dictionary\<string,V>, and the object value is of type MyDictionary\<int32>, passing the `ICorDebugClass` object for Dictionary\<K,V> will successfully get a field of Dictionary\<string,int32>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9dde0-113">需求</span><span class="sxs-lookup"><span data-stu-id="9dde0-113">Requirements</span></span>  
 <span data-ttu-id="9dde0-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9dde0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9dde0-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9dde0-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9dde0-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9dde0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9dde0-117">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9dde0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dde0-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9dde0-118">See also</span></span>
