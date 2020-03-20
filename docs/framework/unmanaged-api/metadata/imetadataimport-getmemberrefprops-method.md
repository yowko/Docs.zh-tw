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
ms.openlocfilehash: a61254ba751e47b0089a3f7528aca337a32e2db3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175365"
---
# <a name="imetadataimportgetmemberrefprops-method"></a><span data-ttu-id="bda45-102">IMetaDataImport::GetMemberRefProps 方法</span><span class="sxs-lookup"><span data-stu-id="bda45-102">IMetaDataImport::GetMemberRefProps Method</span></span>
<span data-ttu-id="bda45-103">取得與指定語彙基元所參考成員相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="bda45-103">Gets metadata associated with the member referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bda45-104">語法</span><span class="sxs-lookup"><span data-stu-id="bda45-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="bda45-105">參數</span><span class="sxs-lookup"><span data-stu-id="bda45-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="bda45-106">[在]要為其返回關聯的中繼資料的會員Ref 權杖。</span><span class="sxs-lookup"><span data-stu-id="bda45-106">[in] The MemberRef token to return associated metadata for.</span></span>  
  
 `ptk`  
 <span data-ttu-id="bda45-107">[出]表示成員聲明的類的 TypeDef 或 TypeRef 或 TypeSpec 權杖，或表示聲明成員的模組類的 ModuleRef 權杖，或表示成員的 MethodDef。</span><span class="sxs-lookup"><span data-stu-id="bda45-107">[out] A TypeDef or TypeRef, or TypeSpec token that represents the class that declares the member, or a ModuleRef token that represents the module class that declares the member, or a MethodDef that represents the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="bda45-108">[出]成員名稱的字串緩衝區。</span><span class="sxs-lookup"><span data-stu-id="bda45-108">[out] A string buffer for the member's name.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="bda45-109">[在]請求的大小以寬字元表示`szMember`。</span><span class="sxs-lookup"><span data-stu-id="bda45-109">[in] The requested size in wide characters of `szMember`.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="bda45-110">[出]返回的大小以寬字元。 `szMember`</span><span class="sxs-lookup"><span data-stu-id="bda45-110">[out] The returned size in wide characters of `szMember`.</span></span>  
  
 `ppvSibBlob`  
 <span data-ttu-id="bda45-111">[出]指向成員的二進位中繼資料簽名的指標。</span><span class="sxs-lookup"><span data-stu-id="bda45-111">[out] A pointer to the binary metadata signature for the member.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="bda45-112">[出]的大小（以位元組為單位）。 `ppvSigBlob`</span><span class="sxs-lookup"><span data-stu-id="bda45-112">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bda45-113">需求</span><span class="sxs-lookup"><span data-stu-id="bda45-113">Requirements</span></span>  
 <span data-ttu-id="bda45-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bda45-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bda45-115">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="bda45-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bda45-116">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="bda45-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bda45-117">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bda45-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bda45-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bda45-118">See also</span></span>

- [<span data-ttu-id="bda45-119">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="bda45-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="bda45-120">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="bda45-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
