---
title: "IMetaDataImport::IsValidToken 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 61af4f5e68ebd5d5e4639cbc4c581d1c66358ff8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportisvalidtoken-method"></a><span data-ttu-id="27abd-102">IMetaDataImport::IsValidToken 方法</span><span class="sxs-lookup"><span data-stu-id="27abd-102">IMetaDataImport::IsValidToken Method</span></span>
<span data-ttu-id="27abd-103">取得一個值，用來表示指定語彙基元是否包含程式碼物件的有效參考。</span><span class="sxs-lookup"><span data-stu-id="27abd-103">Gets a value indicating whether the specified token holds a valid reference to a code object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27abd-104">語法</span><span class="sxs-lookup"><span data-stu-id="27abd-104">Syntax</span></span>  
  
```  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="27abd-105">參數</span><span class="sxs-lookup"><span data-stu-id="27abd-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="27abd-106">[in]若要檢查的參考有效性語彙基元。</span><span class="sxs-lookup"><span data-stu-id="27abd-106">[in] The token to check the reference validity for.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27abd-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="27abd-107">Return Value</span></span>  
 <span data-ttu-id="27abd-108">`true`如果`tk`目前範圍內是有效的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="27abd-108">`true` if `tk` is a valid metadata token within the current scope.</span></span> <span data-ttu-id="27abd-109">否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="27abd-109">Otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27abd-110">需求</span><span class="sxs-lookup"><span data-stu-id="27abd-110">Requirements</span></span>  
 <span data-ttu-id="27abd-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="27abd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27abd-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="27abd-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="27abd-113">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="27abd-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="27abd-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27abd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27abd-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="27abd-115">See Also</span></span>  
 [<span data-ttu-id="27abd-116">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="27abd-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="27abd-117">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="27abd-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
