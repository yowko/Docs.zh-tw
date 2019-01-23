---
title: IMetaDataImport::GetMemberProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberProps
helpviewer_keywords:
- IMetaDataImport::GetMemberProps method [.NET Framework metadata]
- GetMemberProps method [.NET Framework metadata]
ms.assetid: 42790918-4142-4938-b8f4-a56979a55846
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98d7be5adc81cff09b121265e7d5b5f712122607
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611406"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="72068-102">IMetaDataImport::GetMemberProps 方法</span><span class="sxs-lookup"><span data-stu-id="72068-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="72068-103">取得中繼資料資訊，包括名稱、 二進位簽章和相對虛擬位址，<xref:System.Type>指定之中繼資料語彙基元所參考的成員。</span><span class="sxs-lookup"><span data-stu-id="72068-103">Gets metadata information, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72068-104">語法</span><span class="sxs-lookup"><span data-stu-id="72068-104">Syntax</span></span>  
  
```  
HRESULT GetMemberProps (  
   [in]  mdToken           mb,   
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szMember,   
   [in]  ULONG             cchMember,   
   [out] ULONG             *pchMember,   
   [out] DWORD             *pdwAttr,  
   [out] PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pcbSigBlob,   
   [out] ULONG             *pulCodeRVA,   
   [out] DWORD             *pdwImplFlags,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="72068-105">參數</span><span class="sxs-lookup"><span data-stu-id="72068-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="72068-106">[in]參考的成員，以取得相關聯中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="72068-106">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="72068-107">[out]表示的類別成員的中繼資料語彙基元指標。</span><span class="sxs-lookup"><span data-stu-id="72068-107">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="72068-108">[out]成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="72068-108">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="72068-109">[in]寬字元大小`szMember`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="72068-109">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="72068-110">[out]寬字元，傳回的檔案名稱的大小。</span><span class="sxs-lookup"><span data-stu-id="72068-110">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="72068-111">[out]任何旗標套用至成員的值。</span><span class="sxs-lookup"><span data-stu-id="72068-111">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="72068-112">[out]二進位中繼資料簽章的成員指標。</span><span class="sxs-lookup"><span data-stu-id="72068-112">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="72068-113">[out]以位元組為單位的大小`ppvSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="72068-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="72068-114">[out]成員的相對虛擬位址指標。</span><span class="sxs-lookup"><span data-stu-id="72068-114">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="72068-115">[out]成員相關聯任何方法實作旗標。</span><span class="sxs-lookup"><span data-stu-id="72068-115">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="72068-116">[out]標示旗標<xref:System.ValueType>。</span><span class="sxs-lookup"><span data-stu-id="72068-116">[out] A flag that marks a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="72068-117">[out]常數字串值，這個成員所傳回。</span><span class="sxs-lookup"><span data-stu-id="72068-117">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="72068-118">[out]以字元為單位的大小`ppValue`，或零，如果`ppValue`不會保留為字串。</span><span class="sxs-lookup"><span data-stu-id="72068-118">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72068-119">需求</span><span class="sxs-lookup"><span data-stu-id="72068-119">Requirements</span></span>  
 <span data-ttu-id="72068-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="72068-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72068-121">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="72068-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="72068-122">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="72068-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="72068-123">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72068-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72068-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72068-124">See also</span></span>
- [<span data-ttu-id="72068-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="72068-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="72068-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="72068-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
