---
title: "IMetaDataImport::GetUserString 方法"
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
- IMetaDataImport.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetUserString
helpviewer_keywords:
- IMetaDataImport::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 0fd3bb47-58b5-4083-b241-b9719df7a285
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 944d7e6413f35ad56af38dee90dc90f881c1d4cc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetuserstring-method"></a><span data-ttu-id="9e214-102">IMetaDataImport::GetUserString 方法</span><span class="sxs-lookup"><span data-stu-id="9e214-102">IMetaDataImport::GetUserString Method</span></span>
<span data-ttu-id="9e214-103">取得指定中繼資料語彙基元所代表的常值字串。</span><span class="sxs-lookup"><span data-stu-id="9e214-103">Gets the literal string represented by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e214-104">語法</span><span class="sxs-lookup"><span data-stu-id="9e214-104">Syntax</span></span>  
  
```  
HRESULT GetUserString (  
   [in]   mdString    stk,  
   [out]  LPWSTR      szString,  
   [in]   ULONG       cchString,  
   [out]  ULONG       *pchString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9e214-105">參數</span><span class="sxs-lookup"><span data-stu-id="9e214-105">Parameters</span></span>  
 `stk`  
 <span data-ttu-id="9e214-106">[in]傳回相關聯的字串的字串語彙基元。</span><span class="sxs-lookup"><span data-stu-id="9e214-106">[in] The String token to return the associated string for.</span></span>  
  
 `szString`  
 <span data-ttu-id="9e214-107">[out]要求字串的複本。</span><span class="sxs-lookup"><span data-stu-id="9e214-107">[out] A copy of the requested string.</span></span>  
  
 `cchString`  
 <span data-ttu-id="9e214-108">[in]要求的寬字元的最大大小`szString`。</span><span class="sxs-lookup"><span data-stu-id="9e214-108">[in] The maximum size in wide characters of the requested `szString`.</span></span>  
  
 `pchString`  
 <span data-ttu-id="9e214-109">[out]傳回的寬字元大小`szString`。</span><span class="sxs-lookup"><span data-stu-id="9e214-109">[out] The size in wide characters of the returned `szString`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e214-110">需求</span><span class="sxs-lookup"><span data-stu-id="9e214-110">Requirements</span></span>  
 <span data-ttu-id="9e214-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9e214-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e214-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9e214-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9e214-113">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9e214-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9e214-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e214-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e214-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="9e214-115">See Also</span></span>  
 [<span data-ttu-id="9e214-116">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="9e214-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="9e214-117">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="9e214-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
