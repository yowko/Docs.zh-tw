---
title: "IMetaDataAssemblyImport::FindManifestResourceByName 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.FindManifestResourceByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::FindManifestResourceByName
helpviewer_keywords:
- FindManifestResourceByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindManifestResourceByName method [.NET Framework metadata]
ms.assetid: 7b72fa11-3866-402b-bdea-2b966b77cfe0
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 492f8a50c421df56d1b2f79d15d86ef3251b401e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="d425e-102">IMetaDataAssemblyImport::FindManifestResourceByName 方法</span><span class="sxs-lookup"><span data-stu-id="d425e-102">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>
<span data-ttu-id="d425e-103">取得具有指定名稱的資訊清單資源的指標。</span><span class="sxs-lookup"><span data-stu-id="d425e-103">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d425e-104">語法</span><span class="sxs-lookup"><span data-stu-id="d425e-104">Syntax</span></span>  
  
```  
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,   
    [out] mdManifestResource     *ptkManifestResource  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="d425e-105">參數</span><span class="sxs-lookup"><span data-stu-id="d425e-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="d425e-106">[in]資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="d425e-106">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="d425e-107">[out]用來儲存陣列`mdManifestResource`中繼資料語彙基元，其中每一個都代表資訊清單資源。</span><span class="sxs-lookup"><span data-stu-id="d425e-107">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d425e-108">備註</span><span class="sxs-lookup"><span data-stu-id="d425e-108">Remarks</span></span>  
 <span data-ttu-id="d425e-109">`FindManifestResourceByName`方法會使用標準來解析參考的 common language runtime 所採用的規則。</span><span class="sxs-lookup"><span data-stu-id="d425e-109">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d425e-110">需求</span><span class="sxs-lookup"><span data-stu-id="d425e-110">Requirements</span></span>  
 <span data-ttu-id="d425e-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d425e-111">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d425e-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d425e-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d425e-113">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d425e-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d425e-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d425e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d425e-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d425e-115">See Also</span></span>  
 [<span data-ttu-id="d425e-116">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="d425e-116">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="d425e-117">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="d425e-117">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
