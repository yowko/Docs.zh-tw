---
title: IMetaDataImport::GetModuleFromScope 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleFromScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleFromScope
helpviewer_keywords:
- GetModuleFromScope method [.NET Framework metadata]
- IMetaDataImport::GetModuleFromScope method [.NET Framework metadata]
ms.assetid: add68d3f-45fd-4bef-af94-eb5273f26b11
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f40e6bfdbebdadc41da52564348c6070c18372c8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194677"
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="0a032-102">IMetaDataImport::GetModuleFromScope 方法</span><span class="sxs-lookup"><span data-stu-id="0a032-102">IMetaDataImport::GetModuleFromScope Method</span></span>
<span data-ttu-id="0a032-103">取得目前的中繼資料範圍中參考的模組中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="0a032-103">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a032-104">語法</span><span class="sxs-lookup"><span data-stu-id="0a032-104">Syntax</span></span>  
  
```  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a032-105">參數</span><span class="sxs-lookup"><span data-stu-id="0a032-105">Parameters</span></span>  
 `pmd`  
 <span data-ttu-id="0a032-106">[out]代表目前中繼資料範圍內所參考模組的語彙基元指標。</span><span class="sxs-lookup"><span data-stu-id="0a032-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a032-107">需求</span><span class="sxs-lookup"><span data-stu-id="0a032-107">Requirements</span></span>  
 <span data-ttu-id="0a032-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0a032-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a032-109">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0a032-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0a032-110">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0a032-110">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="0a032-111">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="0a032-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0a032-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a032-112">See also</span></span>

- [<span data-ttu-id="0a032-113">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="0a032-113">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="0a032-114">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="0a032-114">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
