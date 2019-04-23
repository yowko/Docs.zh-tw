---
title: IMetaDataImport::GetTypeDefProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeDefProps
helpviewer_keywords:
- GetTypeDefProps method [.NET Framework metadata]
- IMetaDataImport::GetTypeDefProps method [.NET Framework metadata]
ms.assetid: 00061a25-ba05-47a7-b984-fd916b06b149
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a482c7a06efe888408206f2de569e0a8739b85b8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59121507"
---
# <a name="imetadataimportgettypedefprops-method"></a><span data-ttu-id="e2cde-102">IMetaDataImport::GetTypeDefProps 方法</span><span class="sxs-lookup"><span data-stu-id="e2cde-102">IMetaDataImport::GetTypeDefProps Method</span></span>
<span data-ttu-id="e2cde-103">傳回中繼資料資訊<xref:System.Type>指定 TypeDef 語彙基元所代表。</span><span class="sxs-lookup"><span data-stu-id="e2cde-103">Returns metadata information for the <xref:System.Type> represented by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2cde-104">語法</span><span class="sxs-lookup"><span data-stu-id="e2cde-104">Syntax</span></span>  
  
```  
HRESULT GetTypeDefProps (  
   [in]  mdTypeDef   td,  
   [out] LPWSTR      szTypeDef,  
   [in]  ULONG       cchTypeDef,  
   [out] ULONG       *pchTypeDef,  
   [out] DWORD       *pdwTypeDefFlags,  
   [out] mdToken     *ptkExtends  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2cde-105">參數</span><span class="sxs-lookup"><span data-stu-id="e2cde-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="e2cde-106">[in]TypeDef 語彙基元，表示要傳回的中繼資料的型別。</span><span class="sxs-lookup"><span data-stu-id="e2cde-106">[in] The TypeDef token that represents the type to return metadata for.</span></span>  
  
 `szTypeDef`  
 <span data-ttu-id="e2cde-107">[out]緩衝區，包含型別名稱。</span><span class="sxs-lookup"><span data-stu-id="e2cde-107">[out] A buffer containing the type name.</span></span>  
  
 `cchTypeDef`  
 <span data-ttu-id="e2cde-108">[in]寬字元大小`szTypeDef`。</span><span class="sxs-lookup"><span data-stu-id="e2cde-108">[in] The size in wide characters of `szTypeDef`.</span></span>  
  
 `pchTypeDef`  
 <span data-ttu-id="e2cde-109">[out]中傳回的寬字元數目`szTypeDef`。</span><span class="sxs-lookup"><span data-stu-id="e2cde-109">[out] The number of wide characters returned in `szTypeDef`.</span></span>  
  
 `pdwTypeDefFlags`  
 <span data-ttu-id="e2cde-110">[out]若要修改的類型定義任何旗標的指標。</span><span class="sxs-lookup"><span data-stu-id="e2cde-110">[out] A pointer to any flags that modify the type definition.</span></span> <span data-ttu-id="e2cde-111">這個值是從位元遮罩[CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="e2cde-111">This value is a bitmask from the [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration.</span></span>  
  
 `ptkExtends`  
 <span data-ttu-id="e2cde-112">[out]TypeDef 或 TypeRef 中繼資料語彙基元，表示所要求型別的基底型別。</span><span class="sxs-lookup"><span data-stu-id="e2cde-112">[out] A TypeDef or TypeRef metadata token that represents the base type of the requested type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2cde-113">需求</span><span class="sxs-lookup"><span data-stu-id="e2cde-113">Requirements</span></span>  
 <span data-ttu-id="e2cde-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e2cde-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2cde-115">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e2cde-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e2cde-116">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e2cde-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e2cde-117">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2cde-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2cde-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2cde-118">See also</span></span>

- [<span data-ttu-id="e2cde-119">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="e2cde-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="e2cde-120">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="e2cde-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
