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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58a39771bd89fc9c4947f80a3c87b4d340b5461c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934871"
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a><span data-ttu-id="20452-102">ICorDebugAppDomain2::GetArrayOrPointerType 方法</span><span class="sxs-lookup"><span data-stu-id="20452-102">ICorDebugAppDomain2::GetArrayOrPointerType Method</span></span>
<span data-ttu-id="20452-103">取得指定的型別，或是指標或參考指定的型別陣列。</span><span class="sxs-lookup"><span data-stu-id="20452-103">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20452-104">語法</span><span class="sxs-lookup"><span data-stu-id="20452-104">Syntax</span></span>  
  
```  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20452-105">參數</span><span class="sxs-lookup"><span data-stu-id="20452-105">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="20452-106">[in]CorElementType 列舉，指定基礎的原生型別 （陣列、 指標或參考） 若要建立的值。</span><span class="sxs-lookup"><span data-stu-id="20452-106">[in] A value of the CorElementType enumeration that specifies the underlying native type (an array, pointer, or reference) to be created.</span></span>  
  
 `nRank`  
 <span data-ttu-id="20452-107">[in]陣列陣序 （也就是維度的數目）。</span><span class="sxs-lookup"><span data-stu-id="20452-107">[in] The rank (that is, number of dimensions) of the array.</span></span> <span data-ttu-id="20452-108">此值必須是 0，如果`elementType`指定指標或參考類型。</span><span class="sxs-lookup"><span data-stu-id="20452-108">This value must be 0 if `elementType` specifies a pointer or reference type.</span></span>  
  
 `pTypeArg`  
 <span data-ttu-id="20452-109">[in]ICorDebugType 物件，表示陣列類型的指標、 指標或參考來建立。</span><span class="sxs-lookup"><span data-stu-id="20452-109">[in] A pointer to an ICorDebugType object that represents the type of array, pointer, or reference to be created.</span></span>  
  
 `ppType`  
 <span data-ttu-id="20452-110">[out]位址指標`ICorDebugType`代表建構的陣列、 指標類型或參考的物件類型。</span><span class="sxs-lookup"><span data-stu-id="20452-110">[out] A pointer to the address of an `ICorDebugType` object that represents the constructed array, pointer type, or reference type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20452-111">備註</span><span class="sxs-lookup"><span data-stu-id="20452-111">Remarks</span></span>  
 <span data-ttu-id="20452-112">值*elementType*必須是下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="20452-112">The value of *elementType* must be one of the following:</span></span>  
  
- <span data-ttu-id="20452-113">ELEMENT_TYPE_PTR</span><span class="sxs-lookup"><span data-stu-id="20452-113">ELEMENT_TYPE_PTR</span></span>  
  
- <span data-ttu-id="20452-114">ELEMENT_TYPE_BYREF</span><span class="sxs-lookup"><span data-stu-id="20452-114">ELEMENT_TYPE_BYREF</span></span>  
  
- <span data-ttu-id="20452-115">ELEMENT_TYPE_ARRAY 或 ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="20452-115">ELEMENT_TYPE_ARRAY or ELEMENT_TYPE_SZARRAY</span></span>  
  
 <span data-ttu-id="20452-116">如果值*elementType* ELEMENT_TYPE_PTR 或 ELEMENT_TYPE_BYREF， *nRank*必須為零。</span><span class="sxs-lookup"><span data-stu-id="20452-116">If the value of *elementType* is ELEMENT_TYPE_PTR or ELEMENT_TYPE_BYREF, *nRank* must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20452-117">需求</span><span class="sxs-lookup"><span data-stu-id="20452-117">Requirements</span></span>  
 <span data-ttu-id="20452-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="20452-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20452-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="20452-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20452-120">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20452-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20452-121">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20452-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
