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
ms.openlocfilehash: aaaae5bda88d1fbc9949a080c5765127fd112bde
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855962"
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="da5e7-102">IMetaDataAssemblyImport::FindManifestResourceByName 方法</span><span class="sxs-lookup"><span data-stu-id="da5e7-102">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>
<span data-ttu-id="da5e7-103">取得具有指定名稱之資訊清單資源的指標。</span><span class="sxs-lookup"><span data-stu-id="da5e7-103">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da5e7-104">語法</span><span class="sxs-lookup"><span data-stu-id="da5e7-104">Syntax</span></span>  
  
```cpp
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,   
    [out] mdManifestResource     *ptkManifestResource  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="da5e7-105">參數</span><span class="sxs-lookup"><span data-stu-id="da5e7-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="da5e7-106">在資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="da5e7-106">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="da5e7-107">脫銷用來儲存`mdManifestResource`元資料標記的陣列，每個 token 都代表一個資訊清單資源。</span><span class="sxs-lookup"><span data-stu-id="da5e7-107">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da5e7-108">備註</span><span class="sxs-lookup"><span data-stu-id="da5e7-108">Remarks</span></span>  
 <span data-ttu-id="da5e7-109">`FindManifestResourceByName`方法會使用 common language runtime 所採用的標準規則來解析參考。</span><span class="sxs-lookup"><span data-stu-id="da5e7-109">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da5e7-110">需求</span><span class="sxs-lookup"><span data-stu-id="da5e7-110">Requirements</span></span>  
 <span data-ttu-id="da5e7-111">**Platform.object**請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="da5e7-111">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da5e7-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="da5e7-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="da5e7-113">**LIBRARY:** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="da5e7-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="da5e7-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da5e7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da5e7-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da5e7-115">See also</span></span>

- [<span data-ttu-id="da5e7-116">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="da5e7-116">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="da5e7-117">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="da5e7-117">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
