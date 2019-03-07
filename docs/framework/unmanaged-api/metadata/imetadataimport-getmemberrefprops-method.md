---
title: IMetaDataImport::GetMemberRefProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberRefProps
helpviewer_keywords:
- GetMemberRefProps method [.NET Framework metadata]
- IMetaDataImport::GetMemberRefProps method [.NET Framework metadata]
ms.assetid: 0ea73055-ece0-4151-a094-414c88ef8941
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bbc297ce129ba223d85b5e13da1f046b3010f4d3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466020"
---
# <a name="imetadataimportgetmemberrefprops-method"></a><span data-ttu-id="10d5e-102">IMetaDataImport::GetMemberRefProps 方法</span><span class="sxs-lookup"><span data-stu-id="10d5e-102">IMetaDataImport::GetMemberRefProps Method</span></span>
<span data-ttu-id="10d5e-103">取得與指定語彙基元所參考成員相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="10d5e-103">Gets metadata associated with the member referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10d5e-104">語法</span><span class="sxs-lookup"><span data-stu-id="10d5e-104">Syntax</span></span>  
  
```  
HRESULT GetMemberRefProps (  
   [in]  mdMemberRef       mr,   
   [out] mdToken           *ptk,   
   [out] LPWSTR            szMember,   
   [in]  ULONG             cchMember,   
   [out] ULONG             *pchMember,   
   [out] PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pbSig   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10d5e-105">參數</span><span class="sxs-lookup"><span data-stu-id="10d5e-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="10d5e-106">[in]若要傳回相關聯的中繼資料的 MemberRef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="10d5e-106">[in] The MemberRef token to return associated metadata for.</span></span>  
  
 `ptk`  
 <span data-ttu-id="10d5e-107">[out]TypeDef TypeRef 或 TypeSpec 語彙基元，代表宣告的成員或 ModuleRef 語彙基元，代表宣告的成員或代表該成員 MethodDef 的模組類別的類別。</span><span class="sxs-lookup"><span data-stu-id="10d5e-107">[out] A TypeDef or TypeRef, or TypeSpec token that represents the class that declares the member, or a ModuleRef token that represents the module class that declares the member, or a MethodDef that represents the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="10d5e-108">[out]針對成員名稱的字串緩衝區。</span><span class="sxs-lookup"><span data-stu-id="10d5e-108">[out] A string buffer for the member's name.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="10d5e-109">[in]所要求的大小，以寬字元為單位的`szMember`。</span><span class="sxs-lookup"><span data-stu-id="10d5e-109">[in] The requested size in wide characters of `szMember`.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="10d5e-110">[out]寬字元在傳回的大小`szMember`。</span><span class="sxs-lookup"><span data-stu-id="10d5e-110">[out] The returned size in wide characters of `szMember`.</span></span>  
  
 `ppvSibBlob`  
 <span data-ttu-id="10d5e-111">[out]指標，該成員的二進位中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="10d5e-111">[out] A pointer to the binary metadata signature for the member.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="10d5e-112">[out]以位元組為單位的大小`ppvSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="10d5e-112">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10d5e-113">需求</span><span class="sxs-lookup"><span data-stu-id="10d5e-113">Requirements</span></span>  
 <span data-ttu-id="10d5e-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="10d5e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10d5e-115">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="10d5e-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="10d5e-116">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="10d5e-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="10d5e-117">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10d5e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10d5e-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10d5e-118">See also</span></span>
- [<span data-ttu-id="10d5e-119">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="10d5e-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="10d5e-120">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="10d5e-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
