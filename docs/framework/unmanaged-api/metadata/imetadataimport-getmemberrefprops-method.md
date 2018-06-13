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
ms.openlocfilehash: 0d62b9be1bef16014e2870c15a232bb46d4daf10
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448743"
---
# <a name="imetadataimportgetmemberrefprops-method"></a><span data-ttu-id="1a81b-102">IMetaDataImport::GetMemberRefProps 方法</span><span class="sxs-lookup"><span data-stu-id="1a81b-102">IMetaDataImport::GetMemberRefProps Method</span></span>
<span data-ttu-id="1a81b-103">取得與指定語彙基元所參考成員相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="1a81b-103">Gets metadata associated with the member referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a81b-104">語法</span><span class="sxs-lookup"><span data-stu-id="1a81b-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="1a81b-105">參數</span><span class="sxs-lookup"><span data-stu-id="1a81b-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="1a81b-106">[in]要傳回相關聯的中繼資料的 MemberRef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="1a81b-106">[in] The MemberRef token to return associated metadata for.</span></span>  
  
 `ptk`  
 <span data-ttu-id="1a81b-107">[out]TypeDef 或 TypeRef 或 TypeSpec 語彙基元表示宣告成員或表示模組類別宣告成員或代表該成員是 MethodDef ModuleRef 語彙基元的類別。</span><span class="sxs-lookup"><span data-stu-id="1a81b-107">[out] A TypeDef or TypeRef, or TypeSpec token that represents the class that declares the member, or a ModuleRef token that represents the module class that declares the member, or a MethodDef that represents the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="1a81b-108">[out]成員的名稱的的字串緩衝區。</span><span class="sxs-lookup"><span data-stu-id="1a81b-108">[out] A string buffer for the member's name.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="1a81b-109">[in]要求的大小，以寬字元`szMember`。</span><span class="sxs-lookup"><span data-stu-id="1a81b-109">[in] The requested size in wide characters of `szMember`.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="1a81b-110">[out]傳回的大小的寬字元`szMember`。</span><span class="sxs-lookup"><span data-stu-id="1a81b-110">[out] The returned size in wide characters of `szMember`.</span></span>  
  
 `ppvSibBlob`  
 <span data-ttu-id="1a81b-111">[out]成員的二進位中繼資料簽章指標。</span><span class="sxs-lookup"><span data-stu-id="1a81b-111">[out] A pointer to the binary metadata signature for the member.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="1a81b-112">[out]以位元組為單位的大小`ppvSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="1a81b-112">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a81b-113">需求</span><span class="sxs-lookup"><span data-stu-id="1a81b-113">Requirements</span></span>  
 <span data-ttu-id="1a81b-114">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1a81b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a81b-115">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1a81b-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1a81b-116">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1a81b-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1a81b-117">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a81b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a81b-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a81b-118">See Also</span></span>  
 [<span data-ttu-id="1a81b-119">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="1a81b-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="1a81b-120">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="1a81b-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
