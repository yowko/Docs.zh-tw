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
ms.openlocfilehash: 745be25183f6b94e7a807c4230961d72e2836fe5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695331"
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a><span data-ttu-id="521d6-102">ICorDebugObjectValue::GetFieldValue 方法</span><span class="sxs-lookup"><span data-stu-id="521d6-102">ICorDebugObjectValue::GetFieldValue Method</span></span>

<span data-ttu-id="521d6-103">取得這個物件值之指定類別的指定域值。</span><span class="sxs-lookup"><span data-stu-id="521d6-103">Gets the value of the specified field of the specified class for this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="521d6-104">語法</span><span class="sxs-lookup"><span data-stu-id="521d6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="521d6-105">參數</span><span class="sxs-lookup"><span data-stu-id="521d6-105">Parameters</span></span>  

 `pClass`  
 <span data-ttu-id="521d6-106">在"ICorDebugClass" 物件的指標，代表要取得其域值的類別。</span><span class="sxs-lookup"><span data-stu-id="521d6-106">[in] A pointer to an "ICorDebugClass" object that represents the class for which to get the field value.</span></span>  
  
 `fieldDef`  
 <span data-ttu-id="521d6-107">在 `mdFieldDef` 參考描述欄位之中繼資料的權杖。</span><span class="sxs-lookup"><span data-stu-id="521d6-107">[in] An `mdFieldDef` token that references the metadata describing the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="521d6-108">擴展代表指定之欄位值的 "ICorDebugValue" 物件指標。</span><span class="sxs-lookup"><span data-stu-id="521d6-108">[out] A pointer to an "ICorDebugValue" object that represents the value of the specified field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="521d6-109">備註</span><span class="sxs-lookup"><span data-stu-id="521d6-109">Remarks</span></span>  

 <span data-ttu-id="521d6-110">參數中指定的類別 `pClass` 必須在物件值的類別階層中，而且欄位必須是該類別的欄位。</span><span class="sxs-lookup"><span data-stu-id="521d6-110">The class, specified in the `pClass` parameter, must be in the hierarchy of the object value's class, and the field must be a field of that class.</span></span>  
  
 <span data-ttu-id="521d6-111">`GetFieldValue`泛型物件和泛型類別的方法仍然會成功。</span><span class="sxs-lookup"><span data-stu-id="521d6-111">The `GetFieldValue` method will still succeed for generic objects and generic classes.</span></span> <span data-ttu-id="521d6-112">例如，如果 MyDictionary \<V> 繼承自字典 \<string,V> ，而物件值的類型是 MyDictionary，則 \<int32> 傳遞字典的 `ICorDebugClass` 物件 \<K,V> 將會成功取得字典的欄位 \<string,int32> 。</span><span class="sxs-lookup"><span data-stu-id="521d6-112">For example, if MyDictionary\<V> inherits from Dictionary\<string,V>, and the object value is of type MyDictionary\<int32>, passing the `ICorDebugClass` object for Dictionary\<K,V> will successfully get a field of Dictionary\<string,int32>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="521d6-113">需求</span><span class="sxs-lookup"><span data-stu-id="521d6-113">Requirements</span></span>  

 <span data-ttu-id="521d6-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="521d6-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="521d6-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="521d6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="521d6-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="521d6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="521d6-117">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="521d6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="521d6-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="521d6-118">See also</span></span>
