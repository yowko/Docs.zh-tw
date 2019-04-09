---
title: IMetaDataImport::GetUserString 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 358346af540c8b6b7ee1523e763bebbacf8cd2bb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127812"
---
# <a name="imetadataimportgetuserstring-method"></a><span data-ttu-id="92637-102">IMetaDataImport::GetUserString 方法</span><span class="sxs-lookup"><span data-stu-id="92637-102">IMetaDataImport::GetUserString Method</span></span>
<span data-ttu-id="92637-103">取得指定中繼資料語彙基元所代表的常值字串。</span><span class="sxs-lookup"><span data-stu-id="92637-103">Gets the literal string represented by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92637-104">語法</span><span class="sxs-lookup"><span data-stu-id="92637-104">Syntax</span></span>  
  
```  
HRESULT GetUserString (  
   [in]   mdString    stk,  
   [out]  LPWSTR      szString,  
   [in]   ULONG       cchString,  
   [out]  ULONG       *pchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92637-105">參數</span><span class="sxs-lookup"><span data-stu-id="92637-105">Parameters</span></span>  
 `stk`  
 <span data-ttu-id="92637-106">[in]要傳回的相關聯的字串的字串權杖。</span><span class="sxs-lookup"><span data-stu-id="92637-106">[in] The String token to return the associated string for.</span></span>  
  
 `szString`  
 <span data-ttu-id="92637-107">[out]要求字串的複本。</span><span class="sxs-lookup"><span data-stu-id="92637-107">[out] A copy of the requested string.</span></span>  
  
 `cchString`  
 <span data-ttu-id="92637-108">[in]所要求的寬字元的大小上限`szString`。</span><span class="sxs-lookup"><span data-stu-id="92637-108">[in] The maximum size in wide characters of the requested `szString`.</span></span>  
  
 `pchString`  
 <span data-ttu-id="92637-109">[out]傳回寬字元大小`szString`。</span><span class="sxs-lookup"><span data-stu-id="92637-109">[out] The size in wide characters of the returned `szString`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92637-110">需求</span><span class="sxs-lookup"><span data-stu-id="92637-110">Requirements</span></span>  
 <span data-ttu-id="92637-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="92637-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92637-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="92637-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="92637-113">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="92637-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="92637-114">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="92637-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="92637-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92637-115">See also</span></span>

- [<span data-ttu-id="92637-116">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="92637-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="92637-117">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="92637-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
