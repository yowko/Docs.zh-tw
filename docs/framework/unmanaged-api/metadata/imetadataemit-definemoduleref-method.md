---
title: "IMetaDataEmit::DefineModuleRef 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineModuleRef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineModuleRef
helpviewer_keywords:
- DefineModuleRef method [.NET Framework metadata]
- IMetaDataEmit::DefineModuleRef method [.NET Framework metadata]
ms.assetid: f2833594-d90b-4a71-9a53-34b12470c64a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2b3131e6cebf09b0767d1331656ff16b2b55d749
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinemoduleref-method"></a><span data-ttu-id="41aa0-102">IMetaDataEmit::DefineModuleRef 方法</span><span class="sxs-lookup"><span data-stu-id="41aa0-102">IMetaDataEmit::DefineModuleRef Method</span></span>
<span data-ttu-id="41aa0-103">建立具有指定名稱的模組的中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="41aa0-103">Creates the metadata signature for a module with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41aa0-104">語法</span><span class="sxs-lookup"><span data-stu-id="41aa0-104">Syntax</span></span>  
  
```  
HRESULT DefineModuleRef (     
    [in]  LPCWSTR           szName,   
    [out] mdModuleRef       *pmur   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="41aa0-105">參數</span><span class="sxs-lookup"><span data-stu-id="41aa0-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="41aa0-106">[in]其他中繼資料檔案，通常是 DLL 名稱。</span><span class="sxs-lookup"><span data-stu-id="41aa0-106">[in] The name of the other metadata file, typically a DLL.</span></span> <span data-ttu-id="41aa0-107">這是檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="41aa0-107">This is the file name only.</span></span> <span data-ttu-id="41aa0-108">請勿使用完整路徑名稱。</span><span class="sxs-lookup"><span data-stu-id="41aa0-108">Do not use a full path name.</span></span>  
  
 `pmur`  
 <span data-ttu-id="41aa0-109">[out]受指派`mdModuleRef`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="41aa0-109">[out] The assigned `mdModuleRef` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41aa0-110">需求</span><span class="sxs-lookup"><span data-stu-id="41aa0-110">Requirements</span></span>  
 <span data-ttu-id="41aa0-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="41aa0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41aa0-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="41aa0-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="41aa0-113">**程式庫：**做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="41aa0-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41aa0-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41aa0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41aa0-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41aa0-115">See Also</span></span>  
 [<span data-ttu-id="41aa0-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="41aa0-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="41aa0-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="41aa0-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
