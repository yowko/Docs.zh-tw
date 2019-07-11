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
ms.openlocfilehash: a4d8829c9cb2818eafe98809c9a0d5fd8109d076
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778829"
---
# <a name="imetadataimportgettyperefprops-method"></a><span data-ttu-id="a572e-102">IMetaDataImport::GetTypeRefProps 方法</span><span class="sxs-lookup"><span data-stu-id="a572e-102">IMetaDataImport::GetTypeRefProps Method</span></span>
<span data-ttu-id="a572e-103">取得相關聯的中繼資料<xref:System.Type>指定 TypeRef 語彙基元所參考。</span><span class="sxs-lookup"><span data-stu-id="a572e-103">Gets the metadata associated with the <xref:System.Type> referenced by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a572e-104">語法</span><span class="sxs-lookup"><span data-stu-id="a572e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeRefProps (  
   [in]  mdTypeRef   tr,  
   [out] mdToken     *ptkResolutionScope,  
   [out] LPWSTR      szName,  
   [in]  ULONG       cchName,  
   [out] ULONG       *pchName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a572e-105">參數</span><span class="sxs-lookup"><span data-stu-id="a572e-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="a572e-106">[in]TypeRef 語彙基元，表示要傳回的中繼資料的型別。</span><span class="sxs-lookup"><span data-stu-id="a572e-106">[in] The TypeRef token that represents the type to return metadata for.</span></span>  
  
 `ptkResolutionScope`  
 <span data-ttu-id="a572e-107">[out]建立參考的範圍指標。</span><span class="sxs-lookup"><span data-stu-id="a572e-107">[out] A pointer to the scope in which the reference is made.</span></span> <span data-ttu-id="a572e-108">這個值會是一個 AssemblyRef 或 ModuleRef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="a572e-108">This value is an AssemblyRef or ModuleRef token.</span></span>  
  
 `szName`  
 <span data-ttu-id="a572e-109">[out]緩衝區，包含型別名稱。</span><span class="sxs-lookup"><span data-stu-id="a572e-109">[out] A buffer containing the type name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="a572e-110">[in]所要求的大小，以寬字元為單位的`szName`。</span><span class="sxs-lookup"><span data-stu-id="a572e-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="a572e-111">[out]寬字元在傳回的大小`szName`。</span><span class="sxs-lookup"><span data-stu-id="a572e-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a572e-112">需求</span><span class="sxs-lookup"><span data-stu-id="a572e-112">Requirements</span></span>  
 <span data-ttu-id="a572e-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a572e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a572e-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a572e-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a572e-115">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a572e-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a572e-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a572e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a572e-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a572e-117">See also</span></span>

- [<span data-ttu-id="a572e-118">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="a572e-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="a572e-119">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="a572e-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
