---
title: IMetaDataImport::GetTypeRefProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeRefProps
helpviewer_keywords:
- IMetaDataImport::GetTypeRefProps method [.NET Framework metadata]
- GetTypeRefProps method [.NET Framework metadata]
ms.assetid: 01837955-ce1e-4068-b338-fd473bd77d1d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 25482ee81d5210e5ab69007767aecf01435602d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448592"
---
# <a name="imetadataimportgettyperefprops-method"></a><span data-ttu-id="18625-102">IMetaDataImport::GetTypeRefProps 方法</span><span class="sxs-lookup"><span data-stu-id="18625-102">IMetaDataImport::GetTypeRefProps Method</span></span>
<span data-ttu-id="18625-103">取得相關聯的中繼資料<xref:System.Type>指定 TypeRef 語彙基元所參考。</span><span class="sxs-lookup"><span data-stu-id="18625-103">Gets the metadata associated with the <xref:System.Type> referenced by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18625-104">語法</span><span class="sxs-lookup"><span data-stu-id="18625-104">Syntax</span></span>  
  
```  
HRESULT GetTypeRefProps (  
   [in]  mdTypeRef   tr,  
   [out] mdToken     *ptkResolutionScope,  
   [out] LPWSTR      szName,  
   [in]  ULONG       cchName,  
   [out] ULONG       *pchName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="18625-105">參數</span><span class="sxs-lookup"><span data-stu-id="18625-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="18625-106">[in]TypeRef 語彙基元，代表要傳回的中繼資料的類型。</span><span class="sxs-lookup"><span data-stu-id="18625-106">[in] The TypeRef token that represents the type to return metadata for.</span></span>  
  
 `ptkResolutionScope`  
 <span data-ttu-id="18625-107">[out]指標所參考的範圍。</span><span class="sxs-lookup"><span data-stu-id="18625-107">[out] A pointer to the scope in which the reference is made.</span></span> <span data-ttu-id="18625-108">此值為 AssemblyRef 或 ModuleRef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="18625-108">This value is an AssemblyRef or ModuleRef token.</span></span>  
  
 `szName`  
 <span data-ttu-id="18625-109">[out]緩衝區，其中包含的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="18625-109">[out] A buffer containing the type name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="18625-110">[in]要求的大小，以寬字元`szName`。</span><span class="sxs-lookup"><span data-stu-id="18625-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="18625-111">[out]傳回的大小的寬字元`szName`。</span><span class="sxs-lookup"><span data-stu-id="18625-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18625-112">需求</span><span class="sxs-lookup"><span data-stu-id="18625-112">Requirements</span></span>  
 <span data-ttu-id="18625-113">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="18625-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18625-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="18625-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="18625-115">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="18625-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="18625-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18625-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18625-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18625-117">See Also</span></span>  
 [<span data-ttu-id="18625-118">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="18625-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="18625-119">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="18625-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
