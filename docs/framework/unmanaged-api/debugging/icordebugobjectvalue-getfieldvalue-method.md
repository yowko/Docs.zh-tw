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
ms.openlocfilehash: 660bc13e8109994f59444c0adebbc97f54de0b43
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207585"
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a><span data-ttu-id="0c68b-102">ICorDebugObjectValue::GetFieldValue 方法</span><span class="sxs-lookup"><span data-stu-id="0c68b-102">ICorDebugObjectValue::GetFieldValue Method</span></span>
<span data-ttu-id="0c68b-103">取得這個物件值的指定類別之指定欄位的值。</span><span class="sxs-lookup"><span data-stu-id="0c68b-103">Gets the value of the specified field of the specified class for this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c68b-104">語法</span><span class="sxs-lookup"><span data-stu-id="0c68b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c68b-105">參數</span><span class="sxs-lookup"><span data-stu-id="0c68b-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="0c68b-106">在"ICorDebugClass" 物件的指標，代表要取得域值的類別。</span><span class="sxs-lookup"><span data-stu-id="0c68b-106">[in] A pointer to an "ICorDebugClass" object that represents the class for which to get the field value.</span></span>  
  
 `fieldDef`  
 <span data-ttu-id="0c68b-107">在`mdFieldDef`參考描述欄位之中繼資料的 token。</span><span class="sxs-lookup"><span data-stu-id="0c68b-107">[in] An `mdFieldDef` token that references the metadata describing the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="0c68b-108">脫銷代表指定欄位之值的 "ICorDebugValue" 物件指標。</span><span class="sxs-lookup"><span data-stu-id="0c68b-108">[out] A pointer to an "ICorDebugValue" object that represents the value of the specified field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c68b-109">備註</span><span class="sxs-lookup"><span data-stu-id="0c68b-109">Remarks</span></span>  
 <span data-ttu-id="0c68b-110">參數中指定的類別 `pClass` 必須在物件值類別的階層中，而且該欄位必須是該類別的欄位。</span><span class="sxs-lookup"><span data-stu-id="0c68b-110">The class, specified in the `pClass` parameter, must be in the hierarchy of the object value's class, and the field must be a field of that class.</span></span>  
  
 <span data-ttu-id="0c68b-111">`GetFieldValue`泛型物件和泛型類別的方法仍然會成功。</span><span class="sxs-lookup"><span data-stu-id="0c68b-111">The `GetFieldValue` method will still succeed for generic objects and generic classes.</span></span> <span data-ttu-id="0c68b-112">例如，如果 MyDictionary \< v> 繼承自字典 \< 字串、V>，而且物件值的類型為 MyDictionary \< int32>，則傳遞 `ICorDebugClass` 字典 K 的物件， \< V> 將會成功取得字典 \< 字串 int32> 的欄位。</span><span class="sxs-lookup"><span data-stu-id="0c68b-112">For example, if MyDictionary\<V> inherits from Dictionary\<string,V>, and the object value is of type MyDictionary\<int32>, passing the `ICorDebugClass` object for Dictionary\<K,V> will successfully get a field of Dictionary\<string,int32>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c68b-113">需求</span><span class="sxs-lookup"><span data-stu-id="0c68b-113">Requirements</span></span>  
 <span data-ttu-id="0c68b-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0c68b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c68b-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0c68b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c68b-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c68b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c68b-117">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c68b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c68b-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c68b-118">See also</span></span>
