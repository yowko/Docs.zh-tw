---
title: "IMetaDataImport::GetMemberProps 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetMemberProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetMemberProps
helpviewer_keywords:
- IMetaDataImport::GetMemberProps method [.NET Framework metadata]
- GetMemberProps method [.NET Framework metadata]
ms.assetid: 42790918-4142-4938-b8f4-a56979a55846
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 543929390977fc593e86947feece06f43bc0cad6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="11488-102">IMetaDataImport::GetMemberProps 方法</span><span class="sxs-lookup"><span data-stu-id="11488-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="11488-103">取得中繼資料資訊，包括名稱、 二進位簽章和相對虛擬位址的<xref:System.Type>指定的中繼資料語彙基元所參考的成員。</span><span class="sxs-lookup"><span data-stu-id="11488-103">Gets metadata information, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11488-104">語法</span><span class="sxs-lookup"><span data-stu-id="11488-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="11488-105">參數</span><span class="sxs-lookup"><span data-stu-id="11488-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="11488-106">[in]參考成員，以取得相關聯中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="11488-106">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="11488-107">[out]表示類別成員的中繼資料語彙基元的指標。</span><span class="sxs-lookup"><span data-stu-id="11488-107">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="11488-108">[out]成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="11488-108">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="11488-109">[in]中的寬字元大小`szMember`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="11488-109">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="11488-110">[out]傳回名稱的寬字元大小。</span><span class="sxs-lookup"><span data-stu-id="11488-110">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="11488-111">[out]套用至成員的任何旗標值。</span><span class="sxs-lookup"><span data-stu-id="11488-111">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="11488-112">[out]二進位中繼資料簽章的成員指標。</span><span class="sxs-lookup"><span data-stu-id="11488-112">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="11488-113">[out]以位元組為單位的大小`ppvSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="11488-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="11488-114">[out]成員的相對虛擬位址指標。</span><span class="sxs-lookup"><span data-stu-id="11488-114">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="11488-115">[out]成員相關聯任何方法實作旗標。</span><span class="sxs-lookup"><span data-stu-id="11488-115">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="11488-116">[out]標示旗標<xref:System.ValueType>。</span><span class="sxs-lookup"><span data-stu-id="11488-116">[out] A flag that marks a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="11488-117">[out]這個成員所傳回的常數字串值。</span><span class="sxs-lookup"><span data-stu-id="11488-117">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="11488-118">[out]以字元為單位的大小`ppValue`，或如果`ppValue`不會保存一個字串。</span><span class="sxs-lookup"><span data-stu-id="11488-118">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11488-119">需求</span><span class="sxs-lookup"><span data-stu-id="11488-119">Requirements</span></span>  
 <span data-ttu-id="11488-120">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="11488-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11488-121">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="11488-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="11488-122">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="11488-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="11488-123">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11488-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11488-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="11488-124">See Also</span></span>  
 [<span data-ttu-id="11488-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="11488-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="11488-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="11488-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
