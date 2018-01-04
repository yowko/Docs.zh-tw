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
ms.workload: dotnet
ms.openlocfilehash: 2b745e216ca49ed5d226d6d531281880b43e4939
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinemoduleref-method"></a><span data-ttu-id="4265e-102">IMetaDataEmit::DefineModuleRef 方法</span><span class="sxs-lookup"><span data-stu-id="4265e-102">IMetaDataEmit::DefineModuleRef Method</span></span>
<span data-ttu-id="4265e-103">建立具有指定名稱的模組的中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="4265e-103">Creates the metadata signature for a module with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4265e-104">語法</span><span class="sxs-lookup"><span data-stu-id="4265e-104">Syntax</span></span>  
  
```  
HRESULT DefineModuleRef (     
    [in]  LPCWSTR           szName,   
    [out] mdModuleRef       *pmur   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4265e-105">參數</span><span class="sxs-lookup"><span data-stu-id="4265e-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="4265e-106">[in]其他中繼資料檔案，通常是 DLL 名稱。</span><span class="sxs-lookup"><span data-stu-id="4265e-106">[in] The name of the other metadata file, typically a DLL.</span></span> <span data-ttu-id="4265e-107">這是檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="4265e-107">This is the file name only.</span></span> <span data-ttu-id="4265e-108">請勿使用完整路徑名稱。</span><span class="sxs-lookup"><span data-stu-id="4265e-108">Do not use a full path name.</span></span>  
  
 `pmur`  
 <span data-ttu-id="4265e-109">[out]受指派`mdModuleRef`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="4265e-109">[out] The assigned `mdModuleRef` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4265e-110">需求</span><span class="sxs-lookup"><span data-stu-id="4265e-110">Requirements</span></span>  
 <span data-ttu-id="4265e-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4265e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4265e-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4265e-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4265e-113">**程式庫：**做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4265e-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4265e-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4265e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4265e-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="4265e-115">See Also</span></span>  
 [<span data-ttu-id="4265e-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="4265e-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="4265e-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="4265e-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
