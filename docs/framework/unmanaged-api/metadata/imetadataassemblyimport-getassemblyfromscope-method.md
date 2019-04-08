---
title: IMetaDataAssemblyImport::GetAssemblyFromScope 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyFromScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyFromScope
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyFromScope method [.NET Framework metadata]
- GetAssemblyFromScope method [.NET Framework metadata]
ms.assetid: 0b437f70-561d-48c7-abe0-0cb9ace10c08
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7d4797c952bfec4e0863e7a12b97e038c7ff8d95
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191519"
---
# <a name="imetadataassemblyimportgetassemblyfromscope-method"></a><span data-ttu-id="ae9bc-102">IMetaDataAssemblyImport::GetAssemblyFromScope 方法</span><span class="sxs-lookup"><span data-stu-id="ae9bc-102">IMetaDataAssemblyImport::GetAssemblyFromScope Method</span></span>
<span data-ttu-id="ae9bc-103">取得目前範圍中的組件的指標。</span><span class="sxs-lookup"><span data-stu-id="ae9bc-103">Gets a pointer to the assembly in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae9bc-104">語法</span><span class="sxs-lookup"><span data-stu-id="ae9bc-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyFromScope (  
    [out] mdAssembly  *ptkAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae9bc-105">參數</span><span class="sxs-lookup"><span data-stu-id="ae9bc-105">Parameters</span></span>  
 `ptkAssembly`  
 <span data-ttu-id="ae9bc-106">[out]所擷取的指標`mdAssembly`語彙基元，可識別組件。</span><span class="sxs-lookup"><span data-stu-id="ae9bc-106">[out] A pointer to the retrieved `mdAssembly` token that identifies the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae9bc-107">需求</span><span class="sxs-lookup"><span data-stu-id="ae9bc-107">Requirements</span></span>  
 <span data-ttu-id="ae9bc-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ae9bc-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae9bc-109">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ae9bc-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ae9bc-110">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ae9bc-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="ae9bc-111">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="ae9bc-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ae9bc-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae9bc-112">See also</span></span>

- [<span data-ttu-id="ae9bc-113">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="ae9bc-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
