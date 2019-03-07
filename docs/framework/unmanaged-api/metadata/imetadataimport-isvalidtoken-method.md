---
title: IMetaDataImport::IsValidToken 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.IsValidToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::IsValidToken
helpviewer_keywords:
- IMetaDataImport::IsValidToken method [.NET Framework metadata]
- IsValidToken method [.NET Framework metadata]
ms.assetid: aeb0fc63-9eff-4384-9284-cb9900572d74
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6e887fb5f4f9667bed7eef4a84899f82cada0fcd
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489575"
---
# <a name="imetadataimportisvalidtoken-method"></a><span data-ttu-id="42771-102">IMetaDataImport::IsValidToken 方法</span><span class="sxs-lookup"><span data-stu-id="42771-102">IMetaDataImport::IsValidToken Method</span></span>
<span data-ttu-id="42771-103">取得一個值，用來表示指定語彙基元是否包含程式碼物件的有效參考。</span><span class="sxs-lookup"><span data-stu-id="42771-103">Gets a value indicating whether the specified token holds a valid reference to a code object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42771-104">語法</span><span class="sxs-lookup"><span data-stu-id="42771-104">Syntax</span></span>  
  
```  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42771-105">參數</span><span class="sxs-lookup"><span data-stu-id="42771-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="42771-106">[in]若要檢查參考有效的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="42771-106">[in] The token to check the reference validity for.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="42771-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="42771-107">Return Value</span></span>  
 <span data-ttu-id="42771-108">`true` 如果`tk`目前範圍內是有效的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="42771-108">`true` if `tk` is a valid metadata token within the current scope.</span></span> <span data-ttu-id="42771-109">否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="42771-109">Otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42771-110">需求</span><span class="sxs-lookup"><span data-stu-id="42771-110">Requirements</span></span>  
 <span data-ttu-id="42771-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="42771-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42771-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="42771-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="42771-113">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="42771-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="42771-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42771-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42771-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42771-115">See also</span></span>
- [<span data-ttu-id="42771-116">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="42771-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="42771-117">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="42771-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
