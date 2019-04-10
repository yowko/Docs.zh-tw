---
title: IMetaDataImport::GetModuleRefProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleRefProps
helpviewer_keywords:
- GetModuleRefProps method [.NET Framework metadata]
- IMetaDataImport::GetModuleRefProps method [.NET Framework metadata]
ms.assetid: b558e766-4c11-4628-ae47-b4e0a1800168
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e948644e4f2d91b2f1e3e3627f7adbe204dee9d4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59155411"
---
# <a name="imetadataimportgetmodulerefprops-method"></a><span data-ttu-id="d8ced-102">IMetaDataImport::GetModuleRefProps 方法</span><span class="sxs-lookup"><span data-stu-id="d8ced-102">IMetaDataImport::GetModuleRefProps Method</span></span>
<span data-ttu-id="d8ced-103">取得指定中繼資料語彙基元所參考的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="d8ced-103">Gets the name of the module referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8ced-104">語法</span><span class="sxs-lookup"><span data-stu-id="d8ced-104">Syntax</span></span>  
  
```  
HRESULT GetModuleRefProps (  
   [in]  mdModuleRef         mur,  
   [out] LPWSTR              szName,   
   [in]  ULONG               cchName,   
   [out] ULONG               *pchName   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8ced-105">參數</span><span class="sxs-lookup"><span data-stu-id="d8ced-105">Parameters</span></span>  
 `mur`  
 <span data-ttu-id="d8ced-106">[in]ModuleRef 中繼資料語彙基元所參考的模組，以取得中繼資料資訊。</span><span class="sxs-lookup"><span data-stu-id="d8ced-106">[in] The ModuleRef metadata token that references the module to get metadata information for.</span></span>  
  
 `szName`  
 <span data-ttu-id="d8ced-107">[out]緩衝區來容納模組名稱。</span><span class="sxs-lookup"><span data-stu-id="d8ced-107">[out] A buffer to hold the module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="d8ced-108">[in]要求的大小`szName`寬字元。</span><span class="sxs-lookup"><span data-stu-id="d8ced-108">[in] The requested size of `szName` in wide characters.</span></span>  
  
 `pchName`  
 <span data-ttu-id="d8ced-109">[out]傳回的大小`szName`寬字元。</span><span class="sxs-lookup"><span data-stu-id="d8ced-109">[out] The returned size of `szName` in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8ced-110">需求</span><span class="sxs-lookup"><span data-stu-id="d8ced-110">Requirements</span></span>  
 <span data-ttu-id="d8ced-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d8ced-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8ced-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d8ced-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d8ced-113">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d8ced-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="d8ced-114">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="d8ced-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d8ced-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8ced-115">See also</span></span>

- [<span data-ttu-id="d8ced-116">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="d8ced-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="d8ced-117">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="d8ced-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
