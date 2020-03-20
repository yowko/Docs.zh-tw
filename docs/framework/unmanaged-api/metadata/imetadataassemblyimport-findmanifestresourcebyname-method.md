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
ms.openlocfilehash: ae9097725aecd21e910e49a78d81951df39e9b2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177770"
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="8c6c5-102">IMetaDataAssemblyImport::FindManifestResourceByName 方法</span><span class="sxs-lookup"><span data-stu-id="8c6c5-102">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>
<span data-ttu-id="8c6c5-103">獲取指向具有指定名稱的清單資源的指標。</span><span class="sxs-lookup"><span data-stu-id="8c6c5-103">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c6c5-104">語法</span><span class="sxs-lookup"><span data-stu-id="8c6c5-104">Syntax</span></span>  
  
```cpp
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,
    [out] mdManifestResource     *ptkManifestResource  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="8c6c5-105">參數</span><span class="sxs-lookup"><span data-stu-id="8c6c5-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="8c6c5-106">[在]資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="8c6c5-106">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="8c6c5-107">[出]用於存儲中繼資料權杖的`mdManifestResource`陣列，每個權杖都表示一個清單資源。</span><span class="sxs-lookup"><span data-stu-id="8c6c5-107">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c6c5-108">備註</span><span class="sxs-lookup"><span data-stu-id="8c6c5-108">Remarks</span></span>  
 <span data-ttu-id="8c6c5-109">該方法`FindManifestResourceByName`使用通用語言運行時採用的標準規則來解決引用。</span><span class="sxs-lookup"><span data-stu-id="8c6c5-109">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c6c5-110">需求</span><span class="sxs-lookup"><span data-stu-id="8c6c5-110">Requirements</span></span>  
 <span data-ttu-id="8c6c5-111">**平臺：** 請參閱[系統要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8c6c5-111">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c6c5-112">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="8c6c5-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8c6c5-113">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8c6c5-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8c6c5-114">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c6c5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c6c5-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c6c5-115">See also</span></span>

- [<span data-ttu-id="8c6c5-116">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="8c6c5-116">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="8c6c5-117">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="8c6c5-117">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
