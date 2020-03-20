---
title: IMetaDataImport::GetPropertyProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPropertyProps
helpviewer_keywords:
- GetPropertyProps method [.NET Framework metadata]
- IMetaDataImport::GetPropertyProps method [.NET Framework metadata]
ms.assetid: dc0ff3e6-7e7d-4f6c-948d-52b28f5cb78c
topic_type:
- apiref
ms.openlocfilehash: 5fc71bf240b89afadbf8f2ba10906322921bdda2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175326"
---
# <a name="imetadataimportgetpropertyprops-method"></a><span data-ttu-id="396c7-102">IMetaDataImport::GetPropertyProps 方法</span><span class="sxs-lookup"><span data-stu-id="396c7-102">IMetaDataImport::GetPropertyProps Method</span></span>
<span data-ttu-id="396c7-103">獲取指定權杖表示的屬性的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="396c7-103">Gets the metadata for the property represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="396c7-104">語法</span><span class="sxs-lookup"><span data-stu-id="396c7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPropertyProps (  
   [in]  mdProperty        prop,  
   [out] mdTypeDef         *pClass,
   [out] LPCWSTR           szProperty,
   [in]  ULONG             cchProperty,
   [out] ULONG             *pchProperty,
   [out] DWORD             *pdwPropFlags,
   [out] PCCOR_SIGNATURE   *ppvSig,
   [out] ULONG             *pbSig,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppDefaultValue,  
   [out] ULONG             *pcchDefaultValue,  
   [out] mdMethodDef       *pmdSetter,
   [out] mdMethodDef       *pmdGetter,
   [out] mdMethodDef       rmdOtherMethod[],  
   [in]  ULONG             cMax,
   [out] ULONG             *pcOtherMethod
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="396c7-105">參數</span><span class="sxs-lookup"><span data-stu-id="396c7-105">Parameters</span></span>  
 `prop`  
 <span data-ttu-id="396c7-106">[在]表示要為其返回中繼資料的屬性的權杖。</span><span class="sxs-lookup"><span data-stu-id="396c7-106">[in] A token that represents the property to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="396c7-107">[出]指向 TypeDef 權杖的指標，表示實現該屬性的類型。</span><span class="sxs-lookup"><span data-stu-id="396c7-107">[out] A pointer to the TypeDef token that represents the type that implements the property.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="396c7-108">[出]保存屬性名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="396c7-108">[out] A buffer to hold the property name.</span></span>  
  
 `cchProperty`  
 <span data-ttu-id="396c7-109">[在]以 寬字元表示`szProperty`的大小。</span><span class="sxs-lookup"><span data-stu-id="396c7-109">[in] The size in wide characters of `szProperty`.</span></span>  
  
 `pchProperty`  
 <span data-ttu-id="396c7-110">[出]在 中`szProperty`返回的寬字元數。</span><span class="sxs-lookup"><span data-stu-id="396c7-110">[out] The number of wide characters returned in `szProperty`.</span></span>  
  
 `pdwPropFlags`  
 <span data-ttu-id="396c7-111">[出]指向應用於該屬性的任何屬性標誌的指標。</span><span class="sxs-lookup"><span data-stu-id="396c7-111">[out] A pointer to any attribute flags applied to the property.</span></span> <span data-ttu-id="396c7-112">此值是[CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md)枚舉中的位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="396c7-112">This value is a bitmask from the [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) enumeration.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="396c7-113">[出]指向屬性的中繼資料簽名的指標。</span><span class="sxs-lookup"><span data-stu-id="396c7-113">[out] A pointer to the metadata signature of the property.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="396c7-114">[出]在 中`ppvSig`返回的位元組數。</span><span class="sxs-lookup"><span data-stu-id="396c7-114">[out] The number of bytes returned in `ppvSig`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="396c7-115">[出]指定作為屬性預設值的常量類型的標誌。</span><span class="sxs-lookup"><span data-stu-id="396c7-115">[out] A flag specifying the type of the constant that is the default value of the property.</span></span> <span data-ttu-id="396c7-116">此值來自 CorElementType 枚舉。</span><span class="sxs-lookup"><span data-stu-id="396c7-116">This value is from the CorElementType enumeration.</span></span>  
  
 `ppDefaultValue`  
 <span data-ttu-id="396c7-117">[出]指向存儲此屬性的預設值的位元組的指標。</span><span class="sxs-lookup"><span data-stu-id="396c7-117">[out] A pointer to the bytes that store the default value for this property.</span></span>  
  
 `pcchDefaultValue`  
 <span data-ttu-id="396c7-118">[出]大字元的大小`ppDefaultValue`，如果`pdwCPlusTypeFlag`為ELEMENT_TYPE_STRING;否則，此值不相關。</span><span class="sxs-lookup"><span data-stu-id="396c7-118">[out] The size in wide characters of `ppDefaultValue`, if `pdwCPlusTypeFlag` is ELEMENT_TYPE_STRING; otherwise, this value is not relevant.</span></span> <span data-ttu-id="396c7-119">在這種情況下，將從 指定的類型推斷`ppDefaultValue`的長度`pdwCPlusTypeFlag`。</span><span class="sxs-lookup"><span data-stu-id="396c7-119">In that case, the length of `ppDefaultValue` is inferred from the type that is specified by `pdwCPlusTypeFlag`.</span></span>  
  
 `pmdSetter`  
 <span data-ttu-id="396c7-120">[出]指向 MethodDef 權杖的指標，表示屬性的設置訪問器方法。</span><span class="sxs-lookup"><span data-stu-id="396c7-120">[out] A pointer to the MethodDef token that represents the set accessor method for the property.</span></span>  
  
 `pmdGetter`  
 <span data-ttu-id="396c7-121">[出]指向 MethodDef 權杖的指標，表示屬性的 get 訪問器方法。</span><span class="sxs-lookup"><span data-stu-id="396c7-121">[out] A pointer to the MethodDef token that represents the get accessor method for the property.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="396c7-122">[出]表示與屬性關聯的其他方法的 MethodDef 權杖陣列。</span><span class="sxs-lookup"><span data-stu-id="396c7-122">[out] An array of MethodDef tokens that represent other methods associated with the property.</span></span>  
  
 `cMax`  
 <span data-ttu-id="396c7-123">[in] `rmdOtherMethod` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="396c7-123">[in] The maximum size of the `rmdOtherMethod` array.</span></span> <span data-ttu-id="396c7-124">如果提供的陣列足夠大以容納所有方法，則不會發出警告即可跳過這些方法。</span><span class="sxs-lookup"><span data-stu-id="396c7-124">If you do not provide an array large enough to hold all the methods, they are skipped without warning.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="396c7-125">[出]在 中`rmdOtherMethod`返回的 MethodDef 權杖數。</span><span class="sxs-lookup"><span data-stu-id="396c7-125">[out] The number of MethodDef tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="396c7-126">需求</span><span class="sxs-lookup"><span data-stu-id="396c7-126">Requirements</span></span>  
 <span data-ttu-id="396c7-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="396c7-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="396c7-128">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="396c7-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="396c7-129">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="396c7-129">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="396c7-130">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="396c7-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="396c7-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="396c7-131">See also</span></span>

- [<span data-ttu-id="396c7-132">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="396c7-132">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="396c7-133">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="396c7-133">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
