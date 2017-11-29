---
title: "IMetaDataImport::GetModuleRefProps 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetModuleRefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetModuleRefProps
helpviewer_keywords:
- GetModuleRefProps method [.NET Framework metadata]
- IMetaDataImport::GetModuleRefProps method [.NET Framework metadata]
ms.assetid: b558e766-4c11-4628-ae47-b4e0a1800168
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 907743481cf036b7febf57d69ce428a250752c30
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetmodulerefprops-method"></a><span data-ttu-id="4a302-102">IMetaDataImport::GetModuleRefProps 方法</span><span class="sxs-lookup"><span data-stu-id="4a302-102">IMetaDataImport::GetModuleRefProps Method</span></span>
<span data-ttu-id="4a302-103">取得指定中繼資料語彙基元所參考的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="4a302-103">Gets the name of the module referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a302-104">語法</span><span class="sxs-lookup"><span data-stu-id="4a302-104">Syntax</span></span>  
  
```  
HRESULT GetModuleRefProps (  
   [in]  mdModuleRef         mur,  
   [out] LPWSTR              szName,   
   [in]  ULONG               cchName,   
   [out] ULONG               *pchName   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4a302-105">參數</span><span class="sxs-lookup"><span data-stu-id="4a302-105">Parameters</span></span>  
 `mur`  
 <span data-ttu-id="4a302-106">[in]ModuleRef 中繼資料語彙基元所參考的模組取得中繼資料資訊。</span><span class="sxs-lookup"><span data-stu-id="4a302-106">[in] The ModuleRef metadata token that references the module to get metadata information for.</span></span>  
  
 `szName`  
 <span data-ttu-id="4a302-107">[out]緩衝區來保存模組名稱。</span><span class="sxs-lookup"><span data-stu-id="4a302-107">[out] A buffer to hold the module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="4a302-108">[in]要求的大小`szName`寬字元。</span><span class="sxs-lookup"><span data-stu-id="4a302-108">[in] The requested size of `szName` in wide characters.</span></span>  
  
 `pchName`  
 <span data-ttu-id="4a302-109">[out]傳回的大小的`szName`寬字元。</span><span class="sxs-lookup"><span data-stu-id="4a302-109">[out] The returned size of `szName` in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a302-110">需求</span><span class="sxs-lookup"><span data-stu-id="4a302-110">Requirements</span></span>  
 <span data-ttu-id="4a302-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4a302-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a302-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4a302-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4a302-113">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4a302-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4a302-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a302-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a302-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a302-115">See Also</span></span>  
 [<span data-ttu-id="4a302-116">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="4a302-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="4a302-117">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="4a302-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
