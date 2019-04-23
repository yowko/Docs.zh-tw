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
ms.openlocfilehash: 3a99ed42f500b83b5109631b21a88029995b43d6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59123826"
---
# <a name="imetadataimportisvalidtoken-method"></a><span data-ttu-id="e4398-102">IMetaDataImport::IsValidToken 方法</span><span class="sxs-lookup"><span data-stu-id="e4398-102">IMetaDataImport::IsValidToken Method</span></span>
<span data-ttu-id="e4398-103">取得一個值，用來表示指定語彙基元是否包含程式碼物件的有效參考。</span><span class="sxs-lookup"><span data-stu-id="e4398-103">Gets a value indicating whether the specified token holds a valid reference to a code object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4398-104">語法</span><span class="sxs-lookup"><span data-stu-id="e4398-104">Syntax</span></span>  
  
```  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4398-105">參數</span><span class="sxs-lookup"><span data-stu-id="e4398-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="e4398-106">[in]若要檢查參考有效的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e4398-106">[in] The token to check the reference validity for.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e4398-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="e4398-107">Return Value</span></span>  
 <span data-ttu-id="e4398-108">`true` 如果`tk`目前範圍內是有效的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e4398-108">`true` if `tk` is a valid metadata token within the current scope.</span></span> <span data-ttu-id="e4398-109">否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="e4398-109">Otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4398-110">需求</span><span class="sxs-lookup"><span data-stu-id="e4398-110">Requirements</span></span>  
 <span data-ttu-id="e4398-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e4398-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4398-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e4398-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e4398-113">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e4398-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e4398-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4398-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4398-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4398-115">See also</span></span>

- [<span data-ttu-id="e4398-116">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="e4398-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="e4398-117">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="e4398-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
