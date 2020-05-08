---
title: ICorDebugAppDomain2::GetArrayOrPointerType 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2.GetArrayOrPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetArrayOrPointerType
helpviewer_keywords:
- GetArrayOrPointerType method [.NET Framework debugging]
- ICorDebugAppDomain2::GetArrayOrPointerType method [.NET Framework debugging]
ms.assetid: 97e493f5-3a62-4ec7-b42f-4af57bf71f57
topic_type:
- apiref
ms.openlocfilehash: bbf43f3936823b9a8e562cb32cfa2eef08840033
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895192"
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a><span data-ttu-id="527e5-102">ICorDebugAppDomain2::GetArrayOrPointerType 方法</span><span class="sxs-lookup"><span data-stu-id="527e5-102">ICorDebugAppDomain2::GetArrayOrPointerType Method</span></span>
<span data-ttu-id="527e5-103">取得指定類型的陣列，或指定之類型的指標或參考。</span><span class="sxs-lookup"><span data-stu-id="527e5-103">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="527e5-104">語法</span><span class="sxs-lookup"><span data-stu-id="527e5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="527e5-105">參數</span><span class="sxs-lookup"><span data-stu-id="527e5-105">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="527e5-106">在CorElementType 列舉的值，指定要建立的基礎原生類型（陣列、指標或參考）。</span><span class="sxs-lookup"><span data-stu-id="527e5-106">[in] A value of the CorElementType enumeration that specifies the underlying native type (an array, pointer, or reference) to be created.</span></span>  
  
 `nRank`  
 <span data-ttu-id="527e5-107">在陣列的順位（也就是維度的數目）。</span><span class="sxs-lookup"><span data-stu-id="527e5-107">[in] The rank (that is, number of dimensions) of the array.</span></span> <span data-ttu-id="527e5-108">如果`elementType`指定指標或參考型別，這個值必須是0。</span><span class="sxs-lookup"><span data-stu-id="527e5-108">This value must be 0 if `elementType` specifies a pointer or reference type.</span></span>  
  
 `pTypeArg`  
 <span data-ttu-id="527e5-109">在ICorDebugType 物件的指標，代表要建立的陣列、指標或參考的類型。</span><span class="sxs-lookup"><span data-stu-id="527e5-109">[in] A pointer to an ICorDebugType object that represents the type of array, pointer, or reference to be created.</span></span>  
  
 `ppType`  
 <span data-ttu-id="527e5-110">脫銷`ICorDebugType`物件位址的指標，代表結構化陣列、指標類型或參考型別。</span><span class="sxs-lookup"><span data-stu-id="527e5-110">[out] A pointer to the address of an `ICorDebugType` object that represents the constructed array, pointer type, or reference type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="527e5-111">備註</span><span class="sxs-lookup"><span data-stu-id="527e5-111">Remarks</span></span>  
 <span data-ttu-id="527e5-112">*ElementType*的值必須是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="527e5-112">The value of *elementType* must be one of the following:</span></span>  
  
- <span data-ttu-id="527e5-113">ELEMENT_TYPE_PTR</span><span class="sxs-lookup"><span data-stu-id="527e5-113">ELEMENT_TYPE_PTR</span></span>  
  
- <span data-ttu-id="527e5-114">ELEMENT_TYPE_BYREF</span><span class="sxs-lookup"><span data-stu-id="527e5-114">ELEMENT_TYPE_BYREF</span></span>  
  
- <span data-ttu-id="527e5-115">ELEMENT_TYPE_ARRAY 或 ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="527e5-115">ELEMENT_TYPE_ARRAY or ELEMENT_TYPE_SZARRAY</span></span>  
  
 <span data-ttu-id="527e5-116">如果*elementType*的值為 ELEMENT_TYPE_PTR 或 ELEMENT_TYPE_BYREF，則*nRank*必須為零。</span><span class="sxs-lookup"><span data-stu-id="527e5-116">If the value of *elementType* is ELEMENT_TYPE_PTR or ELEMENT_TYPE_BYREF, *nRank* must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="527e5-117">需求</span><span class="sxs-lookup"><span data-stu-id="527e5-117">Requirements</span></span>  
 <span data-ttu-id="527e5-118">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="527e5-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="527e5-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="527e5-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="527e5-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="527e5-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="527e5-121">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="527e5-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
