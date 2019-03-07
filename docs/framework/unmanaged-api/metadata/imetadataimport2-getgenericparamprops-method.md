---
title: IMetaDataImport2::GetGenericParamProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamProps method [.NET Framework metadata]
- GetGenericParamProps method [.NET Framework metadata]
ms.assetid: dbb21e67-712b-49e7-a27c-a1e73ffd46c5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fc2d64a97d02d6f6036646634113cf485119eba7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490355"
---
# <a name="imetadataimport2getgenericparamprops-method"></a><span data-ttu-id="4fbe7-102">IMetaDataImport2::GetGenericParamProps 方法</span><span class="sxs-lookup"><span data-stu-id="4fbe7-102">IMetaDataImport2::GetGenericParamProps Method</span></span>
<span data-ttu-id="4fbe7-103">取得與指定的語彙基元所代表的泛型參數相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="4fbe7-103">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fbe7-104">語法</span><span class="sxs-lookup"><span data-stu-id="4fbe7-104">Syntax</span></span>  
  
```  
HRESULT GetGenericParamProps (  
   [in]  mdGenericParam  gp,  
   [out] ULONG           *pulParamSeq,  
   [out] DWORD           *pdwParamFlags,  
   [out] mdToken         *ptOwner,  
   [out] DWORD           *reserved,  
   [out] LPWSTR          wzName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4fbe7-105">參數</span><span class="sxs-lookup"><span data-stu-id="4fbe7-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="4fbe7-106">[in]表示要傳回的中繼資料的泛型參數的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="4fbe7-106">[in] The token that represents the generic parameter for which to return metadata.</span></span>  
  
 `pulParamSeq`  
 <span data-ttu-id="4fbe7-107">[out]序數位置`Type`父建構函式或方法的參數。</span><span class="sxs-lookup"><span data-stu-id="4fbe7-107">[out] The ordinal position of the `Type` parameter in the parent constructor or method.</span></span>  
  
 `pdwParamFlags`  
 <span data-ttu-id="4fbe7-108">[out]值為[CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md)列舉，可描述`Type`泛型參數。</span><span class="sxs-lookup"><span data-stu-id="4fbe7-108">[out] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the `Type` for the generic parameter.</span></span>  
  
 `ptOwner`  
 <span data-ttu-id="4fbe7-109">[out]TypeDef 或 MethodDef 語彙基元，表示參數的擁有者。</span><span class="sxs-lookup"><span data-stu-id="4fbe7-109">[out] A TypeDef or MethodDef token that represents the owner of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="4fbe7-110">[out]保留供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="4fbe7-110">[out] Reserved for future extensibility.</span></span>  
  
 `wzName`  
 <span data-ttu-id="4fbe7-111">[out]泛型參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fbe7-111">[out] The name of the generic parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="4fbe7-112">[in]大小`wzName`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="4fbe7-112">[in] The size of the `wzName` buffer.</span></span>  
  
 `pchName`  
 <span data-ttu-id="4fbe7-113">[out]傳回的名稱，以寬字元為單位的大小。</span><span class="sxs-lookup"><span data-stu-id="4fbe7-113">[out] The returned size of the name, in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fbe7-114">需求</span><span class="sxs-lookup"><span data-stu-id="4fbe7-114">Requirements</span></span>  
 <span data-ttu-id="4fbe7-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4fbe7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fbe7-116">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4fbe7-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4fbe7-117">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4fbe7-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4fbe7-118">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fbe7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fbe7-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fbe7-119">See also</span></span>
- [<span data-ttu-id="4fbe7-120">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="4fbe7-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="4fbe7-121">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="4fbe7-121">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
