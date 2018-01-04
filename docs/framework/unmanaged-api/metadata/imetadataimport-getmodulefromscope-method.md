---
title: "IMetaDataImport::GetModuleFromScope 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetModuleFromScope
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetModuleFromScope
helpviewer_keywords:
- GetModuleFromScope method [.NET Framework metadata]
- IMetaDataImport::GetModuleFromScope method [.NET Framework metadata]
ms.assetid: add68d3f-45fd-4bef-af94-eb5273f26b11
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b389df634a69bff6197ae11dea96fbb6344dd369
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="1ee9b-102">IMetaDataImport::GetModuleFromScope 方法</span><span class="sxs-lookup"><span data-stu-id="1ee9b-102">IMetaDataImport::GetModuleFromScope Method</span></span>
<span data-ttu-id="1ee9b-103">取得目前中繼資料範圍中參考的模組中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="1ee9b-103">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ee9b-104">語法</span><span class="sxs-lookup"><span data-stu-id="1ee9b-104">Syntax</span></span>  
  
```  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ee9b-105">參數</span><span class="sxs-lookup"><span data-stu-id="1ee9b-105">Parameters</span></span>  
 `pmd`  
 <span data-ttu-id="1ee9b-106">[out]代表目前中繼資料範圍中所參考的模組語彙基元的指標。</span><span class="sxs-lookup"><span data-stu-id="1ee9b-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ee9b-107">需求</span><span class="sxs-lookup"><span data-stu-id="1ee9b-107">Requirements</span></span>  
 <span data-ttu-id="1ee9b-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1ee9b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ee9b-109">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1ee9b-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1ee9b-110">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1ee9b-110">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1ee9b-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ee9b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ee9b-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="1ee9b-112">See Also</span></span>  
 [<span data-ttu-id="1ee9b-113">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="1ee9b-113">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="1ee9b-114">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="1ee9b-114">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
