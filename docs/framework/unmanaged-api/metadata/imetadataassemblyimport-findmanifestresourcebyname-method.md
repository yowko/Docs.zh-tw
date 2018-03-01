---
title: "IMetaDataAssemblyImport::FindManifestResourceByName 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2d6cc738c227157b45e242fb46a672d28d6ce778
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="66624-102">IMetaDataAssemblyImport::FindManifestResourceByName 方法</span><span class="sxs-lookup"><span data-stu-id="66624-102">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>
<span data-ttu-id="66624-103">取得具有指定名稱的資訊清單資源的指標。</span><span class="sxs-lookup"><span data-stu-id="66624-103">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66624-104">語法</span><span class="sxs-lookup"><span data-stu-id="66624-104">Syntax</span></span>  
  
```  
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,   
    [out] mdManifestResource     *ptkManifestResource  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="66624-105">參數</span><span class="sxs-lookup"><span data-stu-id="66624-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="66624-106">[in]資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="66624-106">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="66624-107">[out]用來儲存陣列`mdManifestResource`中繼資料語彙基元，其中每一個都代表資訊清單資源。</span><span class="sxs-lookup"><span data-stu-id="66624-107">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66624-108">備註</span><span class="sxs-lookup"><span data-stu-id="66624-108">Remarks</span></span>  
 <span data-ttu-id="66624-109">`FindManifestResourceByName`方法會使用標準來解析參考的 common language runtime 所採用的規則。</span><span class="sxs-lookup"><span data-stu-id="66624-109">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66624-110">需求</span><span class="sxs-lookup"><span data-stu-id="66624-110">Requirements</span></span>  
 <span data-ttu-id="66624-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="66624-111">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66624-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="66624-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="66624-113">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="66624-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="66624-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66624-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66624-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="66624-115">See Also</span></span>  
 [<span data-ttu-id="66624-116">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="66624-116">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="66624-117">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="66624-117">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
