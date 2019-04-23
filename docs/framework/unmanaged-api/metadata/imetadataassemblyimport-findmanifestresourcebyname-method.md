---
title: IMetaDataAssemblyImport::FindManifestResourceByName 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindManifestResourceByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindManifestResourceByName
helpviewer_keywords:
- FindManifestResourceByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindManifestResourceByName method [.NET Framework metadata]
ms.assetid: 7b72fa11-3866-402b-bdea-2b966b77cfe0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bf61da362251577acadb83915404eba7508b3099
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59141566"
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="9a38e-102">IMetaDataAssemblyImport::FindManifestResourceByName 方法</span><span class="sxs-lookup"><span data-stu-id="9a38e-102">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>
<span data-ttu-id="9a38e-103">取得具有指定名稱的資訊清單資源的指標。</span><span class="sxs-lookup"><span data-stu-id="9a38e-103">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a38e-104">語法</span><span class="sxs-lookup"><span data-stu-id="9a38e-104">Syntax</span></span>  
  
```  
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,   
    [out] mdManifestResource     *ptkManifestResource  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="9a38e-105">參數</span><span class="sxs-lookup"><span data-stu-id="9a38e-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="9a38e-106">[in]資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="9a38e-106">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="9a38e-107">[out]用來儲存陣列`mdManifestResource`中繼資料語彙基元，每一個都代表資訊清單資源。</span><span class="sxs-lookup"><span data-stu-id="9a38e-107">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a38e-108">備註</span><span class="sxs-lookup"><span data-stu-id="9a38e-108">Remarks</span></span>  
 <span data-ttu-id="9a38e-109">`FindManifestResourceByName`方法會使用解析參考的 common language runtime 所採用的標準規則。</span><span class="sxs-lookup"><span data-stu-id="9a38e-109">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a38e-110">需求</span><span class="sxs-lookup"><span data-stu-id="9a38e-110">Requirements</span></span>  
 <span data-ttu-id="9a38e-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9a38e-111">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a38e-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9a38e-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9a38e-113">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9a38e-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9a38e-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a38e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a38e-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a38e-115">See also</span></span>

- [<span data-ttu-id="9a38e-116">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="9a38e-116">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="9a38e-117">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="9a38e-117">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
