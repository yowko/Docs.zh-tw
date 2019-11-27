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
ms.openlocfilehash: 247a2793bf3806f5ee38585d50b4535820dfcb69
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437067"
---
# <a name="imetadataimportgetpropertyprops-method"></a><span data-ttu-id="ded91-102">IMetaDataImport::GetPropertyProps 方法</span><span class="sxs-lookup"><span data-stu-id="ded91-102">IMetaDataImport::GetPropertyProps Method</span></span>
<span data-ttu-id="ded91-103">取得指定標記所表示之屬性的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="ded91-103">Gets the metadata for the property represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ded91-104">語法</span><span class="sxs-lookup"><span data-stu-id="ded91-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ded91-105">參數</span><span class="sxs-lookup"><span data-stu-id="ded91-105">Parameters</span></span>  
 `prop`  
 <span data-ttu-id="ded91-106">在Token，表示要傳回中繼資料的屬性。</span><span class="sxs-lookup"><span data-stu-id="ded91-106">[in] A token that represents the property to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="ded91-107">脫銷TypeDef token 的指標，代表實作為屬性的型別。</span><span class="sxs-lookup"><span data-stu-id="ded91-107">[out] A pointer to the TypeDef token that represents the type that implements the property.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="ded91-108">脫銷保存屬性名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ded91-108">[out] A buffer to hold the property name.</span></span>  
  
 `cchProperty`  
 <span data-ttu-id="ded91-109">在`szProperty`的寬字元大小。</span><span class="sxs-lookup"><span data-stu-id="ded91-109">[in] The size in wide characters of `szProperty`.</span></span>  
  
 `pchProperty`  
 <span data-ttu-id="ded91-110">脫銷`szProperty`中傳回的寬字元數。</span><span class="sxs-lookup"><span data-stu-id="ded91-110">[out] The number of wide characters returned in `szProperty`.</span></span>  
  
 `pdwPropFlags`  
 <span data-ttu-id="ded91-111">脫銷套用至屬性之任何屬性旗標的指標。</span><span class="sxs-lookup"><span data-stu-id="ded91-111">[out] A pointer to any attribute flags applied to the property.</span></span> <span data-ttu-id="ded91-112">這個值是[CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md)列舉中的位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="ded91-112">This value is a bitmask from the [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) enumeration.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="ded91-113">脫銷屬性之中繼資料簽章的指標。</span><span class="sxs-lookup"><span data-stu-id="ded91-113">[out] A pointer to the metadata signature of the property.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="ded91-114">脫銷`ppvSig`中傳回的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="ded91-114">[out] The number of bytes returned in `ppvSig`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="ded91-115">脫銷指定常數類型的旗標，其為屬性的預設值。</span><span class="sxs-lookup"><span data-stu-id="ded91-115">[out] A flag specifying the type of the constant that is the default value of the property.</span></span> <span data-ttu-id="ded91-116">此值來自 CorElementType 列舉。</span><span class="sxs-lookup"><span data-stu-id="ded91-116">This value is from the CorElementType enumeration.</span></span>  
  
 `ppDefaultValue`  
 <span data-ttu-id="ded91-117">脫銷儲存這個屬性之預設值的位元組指標。</span><span class="sxs-lookup"><span data-stu-id="ded91-117">[out] A pointer to the bytes that store the default value for this property.</span></span>  
  
 `pcchDefaultValue`  
 <span data-ttu-id="ded91-118">脫銷`ppDefaultValue`的寬字元大小（如果 `pdwCPlusTypeFlag` ELEMENT_TYPE_STRING）;否則，這個值就是不相關的。</span><span class="sxs-lookup"><span data-stu-id="ded91-118">[out] The size in wide characters of `ppDefaultValue`, if `pdwCPlusTypeFlag` is ELEMENT_TYPE_STRING; otherwise, this value is not relevant.</span></span> <span data-ttu-id="ded91-119">在這種情況下，`ppDefaultValue` 的長度是從 `pdwCPlusTypeFlag`所指定的類型推斷而來。</span><span class="sxs-lookup"><span data-stu-id="ded91-119">In that case, the length of `ppDefaultValue` is inferred from the type that is specified by `pdwCPlusTypeFlag`.</span></span>  
  
 `pmdSetter`  
 <span data-ttu-id="ded91-120">脫銷MethodDef token 的指標，表示屬性的 set 存取子方法。</span><span class="sxs-lookup"><span data-stu-id="ded91-120">[out] A pointer to the MethodDef token that represents the set accessor method for the property.</span></span>  
  
 `pmdGetter`  
 <span data-ttu-id="ded91-121">脫銷MethodDef token 的指標，表示屬性的 get 存取子方法。</span><span class="sxs-lookup"><span data-stu-id="ded91-121">[out] A pointer to the MethodDef token that represents the get accessor method for the property.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="ded91-122">脫銷MethodDef 標記的陣列，表示與屬性相關聯的其他方法。</span><span class="sxs-lookup"><span data-stu-id="ded91-122">[out] An array of MethodDef tokens that represent other methods associated with the property.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ded91-123">[in] `rmdOtherMethod` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="ded91-123">[in] The maximum size of the `rmdOtherMethod` array.</span></span> <span data-ttu-id="ded91-124">如果您未提供足夠大的陣列來保存所有方法，則會略過，而不發出警告。</span><span class="sxs-lookup"><span data-stu-id="ded91-124">If you do not provide an array large enough to hold all the methods, they are skipped without warning.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="ded91-125">脫銷`rmdOtherMethod`中傳回的 MethodDef 權杖數目。</span><span class="sxs-lookup"><span data-stu-id="ded91-125">[out] The number of MethodDef tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ded91-126">需求</span><span class="sxs-lookup"><span data-stu-id="ded91-126">Requirements</span></span>  
 <span data-ttu-id="ded91-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ded91-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ded91-128">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="ded91-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ded91-129">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ded91-129">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ded91-130">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ded91-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ded91-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ded91-131">See also</span></span>

- [<span data-ttu-id="ded91-132">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="ded91-132">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="ded91-133">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="ded91-133">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
