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
ms.openlocfilehash: 9afc2ecc34131f62f1f8e8e86ca73f8b8b0126b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443508"
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="3f024-102">IMetaDataAssemblyImport::FindManifestResourceByName 方法</span><span class="sxs-lookup"><span data-stu-id="3f024-102">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>
<span data-ttu-id="3f024-103">取得具有指定名稱的資訊清單資源的指標。</span><span class="sxs-lookup"><span data-stu-id="3f024-103">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f024-104">語法</span><span class="sxs-lookup"><span data-stu-id="3f024-104">Syntax</span></span>  
  
```  
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,   
    [out] mdManifestResource     *ptkManifestResource  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="3f024-105">參數</span><span class="sxs-lookup"><span data-stu-id="3f024-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="3f024-106">[in]資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="3f024-106">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="3f024-107">[out]用來儲存陣列`mdManifestResource`中繼資料語彙基元，其中每一個都代表資訊清單資源。</span><span class="sxs-lookup"><span data-stu-id="3f024-107">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f024-108">備註</span><span class="sxs-lookup"><span data-stu-id="3f024-108">Remarks</span></span>  
 <span data-ttu-id="3f024-109">`FindManifestResourceByName`方法會使用標準來解析參考的 common language runtime 所採用的規則。</span><span class="sxs-lookup"><span data-stu-id="3f024-109">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f024-110">需求</span><span class="sxs-lookup"><span data-stu-id="3f024-110">Requirements</span></span>  
 <span data-ttu-id="3f024-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3f024-111">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f024-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3f024-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3f024-113">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3f024-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3f024-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f024-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f024-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f024-115">See Also</span></span>  
 [<span data-ttu-id="3f024-116">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="3f024-116">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="3f024-117">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="3f024-117">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
