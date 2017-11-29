---
title: "IMetaDataAssemblyImport::EnumManifestResources 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.EnumManifestResources
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::EnumManifestResources
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumManifestResources method [.NET Framework metadata]
- EnumManifestResources method [.NET Framework metadata]
ms.assetid: 9543b111-5705-40c9-935c-a3ffc7a581aa
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 25d8b63e2f40566164274715e562960eafbb83e5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a><span data-ttu-id="7d120-102">IMetaDataAssemblyImport::EnumManifestResources 方法</span><span class="sxs-lookup"><span data-stu-id="7d120-102">IMetaDataAssemblyImport::EnumManifestResources Method</span></span>
<span data-ttu-id="7d120-103">取得列舉值的指標，在目前的組件資訊清單所參考的資源。</span><span class="sxs-lookup"><span data-stu-id="7d120-103">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d120-104">語法</span><span class="sxs-lookup"><span data-stu-id="7d120-104">Syntax</span></span>  
  
```  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,   
    [out] mdManifestResource   rManifestResources[],   
    [in]  ULONG                cMax,   
    [out] ULONG                *pcTokens  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="7d120-105">參數</span><span class="sxs-lookup"><span data-stu-id="7d120-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="7d120-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="7d120-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="7d120-107">這必須是 null 值時`EnumManifestResources`第一次呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="7d120-107">This must be a null value when the `EnumManifestResources` method is called for the first time.</span></span>  
  
 `rManifestResources`  
 <span data-ttu-id="7d120-108">[out]用來儲存陣列`mdManifestResource`中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="7d120-108">[out] The array used to store the `mdManifestResource` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="7d120-109">[in]最大數目`mdManifestResource`可以放入權杖`rManifestResources`。</span><span class="sxs-lookup"><span data-stu-id="7d120-109">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="7d120-110">[out]數目`mdManifestResource`語彙基元實際置於`rManifestResources`。</span><span class="sxs-lookup"><span data-stu-id="7d120-110">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d120-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="7d120-111">Return Value</span></span>  
  
|<span data-ttu-id="7d120-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7d120-112">HRESULT</span></span>|<span data-ttu-id="7d120-113">說明</span><span class="sxs-lookup"><span data-stu-id="7d120-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="7d120-114">`EnumManifestResources`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="7d120-114">`EnumManifestResources` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="7d120-115">沒有列舉語彙基元。</span><span class="sxs-lookup"><span data-stu-id="7d120-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="7d120-116">在此情況下，`pcTokens`設為零。</span><span class="sxs-lookup"><span data-stu-id="7d120-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7d120-117">需求</span><span class="sxs-lookup"><span data-stu-id="7d120-117">Requirements</span></span>  
 <span data-ttu-id="7d120-118">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7d120-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d120-119">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7d120-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7d120-120">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7d120-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7d120-121">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d120-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d120-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d120-122">See Also</span></span>  
 [<span data-ttu-id="7d120-123">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="7d120-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
