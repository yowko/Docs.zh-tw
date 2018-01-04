---
title: "IMetaDataAssemblyEmit::SetManifestResourceProps 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.SetManifestResourceProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::SetManifestResourceProps
helpviewer_keywords:
- SetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetManifestResourceProps method [.NET Framework metadata]
ms.assetid: ef77efd1-849c-4e51-ba92-7ee3d2bf0339
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e6649b8f82031699692a0929b5483ba57147399b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a><span data-ttu-id="a3a4e-102">IMetaDataAssemblyEmit::SetManifestResourceProps 方法</span><span class="sxs-lookup"><span data-stu-id="a3a4e-102">IMetaDataAssemblyEmit::SetManifestResourceProps Method</span></span>
<span data-ttu-id="a3a4e-103">修改指定的 `ManifestResource` 中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="a3a4e-103">Modifies the specified `ManifestResource` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3a4e-104">語法</span><span class="sxs-lookup"><span data-stu-id="a3a4e-104">Syntax</span></span>  
  
```  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,   
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a3a4e-105">參數</span><span class="sxs-lookup"><span data-stu-id="a3a4e-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="a3a4e-106">[in]指定的語彙基元`ManifestResource`要修改的中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="a3a4e-106">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="a3a4e-107">[in]類型的語彙基元`File`或`AssemblyRef`，可對應到資源提供者。</span><span class="sxs-lookup"><span data-stu-id="a3a4e-107">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="a3a4e-108">[in]資源檔內的開頭位移。</span><span class="sxs-lookup"><span data-stu-id="a3a4e-108">[in] The offset to the beginning of the resource within the file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="a3a4e-109">[in]指定的資源屬性的旗標值的位元組合。</span><span class="sxs-lookup"><span data-stu-id="a3a4e-109">[in] A bitwise combination of flag values that specify the attributes of the resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3a4e-110">備註</span><span class="sxs-lookup"><span data-stu-id="a3a4e-110">Remarks</span></span>  
 <span data-ttu-id="a3a4e-111">若要建立`ManifestResource`中繼資料結構，使用[imetadataassemblyemit:: Definemanifestresource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="a3a4e-111">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3a4e-112">需求</span><span class="sxs-lookup"><span data-stu-id="a3a4e-112">Requirements</span></span>  
 <span data-ttu-id="a3a4e-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a3a4e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3a4e-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a3a4e-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a3a4e-115">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a3a4e-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a3a4e-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3a4e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3a4e-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="a3a4e-117">See Also</span></span>  
 [<span data-ttu-id="a3a4e-118">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="a3a4e-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
