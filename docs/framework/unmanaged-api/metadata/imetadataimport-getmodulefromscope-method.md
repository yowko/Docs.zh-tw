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
ms.openlocfilehash: 1118c29acd926821e3b5db31694df9935bdefb9e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468802"
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="73c85-102">IMetaDataImport::GetModuleFromScope 方法</span><span class="sxs-lookup"><span data-stu-id="73c85-102">IMetaDataImport::GetModuleFromScope Method</span></span>
<span data-ttu-id="73c85-103">取得目前的中繼資料範圍中參考的模組中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="73c85-103">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73c85-104">語法</span><span class="sxs-lookup"><span data-stu-id="73c85-104">Syntax</span></span>  
  
```  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73c85-105">參數</span><span class="sxs-lookup"><span data-stu-id="73c85-105">Parameters</span></span>  
 `pmd`  
 <span data-ttu-id="73c85-106">[out]代表目前中繼資料範圍內所參考模組的語彙基元指標。</span><span class="sxs-lookup"><span data-stu-id="73c85-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73c85-107">需求</span><span class="sxs-lookup"><span data-stu-id="73c85-107">Requirements</span></span>  
 <span data-ttu-id="73c85-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="73c85-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73c85-109">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="73c85-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="73c85-110">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="73c85-110">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="73c85-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73c85-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73c85-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73c85-112">See also</span></span>
- [<span data-ttu-id="73c85-113">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="73c85-113">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="73c85-114">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="73c85-114">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
