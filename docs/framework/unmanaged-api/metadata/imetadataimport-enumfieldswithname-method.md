---
title: IMetaDataImport::EnumFieldsWithName 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFieldsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFieldsWithName
helpviewer_keywords:
- IMetaDataImport::EnumFieldsWithName method [.NET Framework metadata]
- EnumFieldsWithName method [.NET Framework metadata]
ms.assetid: 42145e8d-000f-4d0b-ae43-c08201190fa2
topic_type:
- apiref
ms.openlocfilehash: 68261b165847a5c3ee29adbc4908451fb00c5443
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492261"
---
# <a name="imetadataimportenumfieldswithname-method"></a><span data-ttu-id="83f76-102">IMetaDataImport::EnumFieldsWithName 方法</span><span class="sxs-lookup"><span data-stu-id="83f76-102">IMetaDataImport::EnumFieldsWithName Method</span></span>
<span data-ttu-id="83f76-103">列舉具有指定名稱之指定類型的 FieldDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="83f76-103">Enumerates FieldDef tokens of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83f76-104">語法</span><span class="sxs-lookup"><span data-stu-id="83f76-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFieldsWithName (  
   [in, out] HCORENUM    *phEnum,
   [in]  mdTypeDef       cl,
   [in]  LPCWSTR         szName,
   [out] mdFieldDef      rFields[],
   [in]  ULONG           cMax,
   [out] ULONG           *pcTokens
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83f76-105">參數</span><span class="sxs-lookup"><span data-stu-id="83f76-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="83f76-106">[in、out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="83f76-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="83f76-107">在要列舉其欄位之類型的 token。</span><span class="sxs-lookup"><span data-stu-id="83f76-107">[in] The token of the type whose fields are to be enumerated.</span></span>  
  
 `szName`  
 <span data-ttu-id="83f76-108">在限制列舉範圍的功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="83f76-108">[in] The field name that limits the scope of the enumeration.</span></span>  
  
 `rFields`  
 <span data-ttu-id="83f76-109">脫銷用來儲存 FieldDef 標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="83f76-109">[out] Array used to store the FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="83f76-110">[in] `rFields` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="83f76-110">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="83f76-111">脫銷在中傳回的 FieldDef token 實際數目 `rFields` 。</span><span class="sxs-lookup"><span data-stu-id="83f76-111">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83f76-112">備註</span><span class="sxs-lookup"><span data-stu-id="83f76-112">Remarks</span></span>  
 <span data-ttu-id="83f76-113">不同于[IMetaDataImport：： EnumFields](imetadataimport-enumfields-method.md)，會 `EnumFieldsWithName` 捨棄所有沒有指定名稱的欄位標記。</span><span class="sxs-lookup"><span data-stu-id="83f76-113">Unlike [IMetaDataImport::EnumFields](imetadataimport-enumfields-method.md), `EnumFieldsWithName` discards all field tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83f76-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="83f76-114">Return Value</span></span>  
  
|<span data-ttu-id="83f76-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="83f76-115">HRESULT</span></span>|<span data-ttu-id="83f76-116">說明</span><span class="sxs-lookup"><span data-stu-id="83f76-116">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="83f76-117">`EnumFieldsWithName`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="83f76-117">`EnumFieldsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="83f76-118">沒有可列舉的欄位。</span><span class="sxs-lookup"><span data-stu-id="83f76-118">There are no fields to enumerate.</span></span> <span data-ttu-id="83f76-119">在此情況下， `pcTokens` 是零。</span><span class="sxs-lookup"><span data-stu-id="83f76-119">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="83f76-120">規格需求</span><span class="sxs-lookup"><span data-stu-id="83f76-120">Requirements</span></span>  
 <span data-ttu-id="83f76-121">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="83f76-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83f76-122">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="83f76-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="83f76-123">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="83f76-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="83f76-124">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83f76-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83f76-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83f76-125">See also</span></span>

- [<span data-ttu-id="83f76-126">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="83f76-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="83f76-127">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="83f76-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
