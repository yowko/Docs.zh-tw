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
ms.openlocfilehash: 3237b67f8f711e9ef213d6fc66f1513c534fbdeb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733200"
---
# <a name="imetadataimportgetmemberrefprops-method"></a><span data-ttu-id="c5b87-102">IMetaDataImport::GetMemberRefProps 方法</span><span class="sxs-lookup"><span data-stu-id="c5b87-102">IMetaDataImport::GetMemberRefProps Method</span></span>

<span data-ttu-id="c5b87-103">取得與指定語彙基元所參考成員相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c5b87-103">Gets metadata associated with the member referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5b87-104">語法</span><span class="sxs-lookup"><span data-stu-id="c5b87-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="c5b87-105">參數</span><span class="sxs-lookup"><span data-stu-id="c5b87-105">Parameters</span></span>  

 `mr`  
 <span data-ttu-id="c5b87-106">在要傳回相關聯中繼資料的 MemberRef 標記。</span><span class="sxs-lookup"><span data-stu-id="c5b87-106">[in] The MemberRef token to return associated metadata for.</span></span>  
  
 `ptk`  
 <span data-ttu-id="c5b87-107">擴展TypeDef 或 TypeRef 或 TypeSpec token，表示宣告成員的類別，或代表宣告成員之模組類別的 ModuleRef token，或代表成員的 MethodDef。</span><span class="sxs-lookup"><span data-stu-id="c5b87-107">[out] A TypeDef or TypeRef, or TypeSpec token that represents the class that declares the member, or a ModuleRef token that represents the module class that declares the member, or a MethodDef that represents the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="c5b87-108">擴展成員名稱的字串緩衝區。</span><span class="sxs-lookup"><span data-stu-id="c5b87-108">[out] A string buffer for the member's name.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="c5b87-109">在要求的大小（以寬字元為單位） `szMember` 。</span><span class="sxs-lookup"><span data-stu-id="c5b87-109">[in] The requested size in wide characters of `szMember`.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="c5b87-110">擴展傳回的大小（以寬字元為單位） `szMember` 。</span><span class="sxs-lookup"><span data-stu-id="c5b87-110">[out] The returned size in wide characters of `szMember`.</span></span>  
  
 `ppvSibBlob`  
 <span data-ttu-id="c5b87-111">擴展成員的二進位中繼資料簽章指標。</span><span class="sxs-lookup"><span data-stu-id="c5b87-111">[out] A pointer to the binary metadata signature for the member.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="c5b87-112">擴展的大小（以位元組為單位） `ppvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="c5b87-112">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5b87-113">需求</span><span class="sxs-lookup"><span data-stu-id="c5b87-113">Requirements</span></span>  

 <span data-ttu-id="c5b87-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c5b87-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5b87-115">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="c5b87-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c5b87-116">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="c5b87-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c5b87-117">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5b87-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5b87-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5b87-118">See also</span></span>

- [<span data-ttu-id="c5b87-119">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="c5b87-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="c5b87-120">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="c5b87-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
