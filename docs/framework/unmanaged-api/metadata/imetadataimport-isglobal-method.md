---
title: IMetaDataImport::IsGlobal 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.IsGlobal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::IsGlobal
helpviewer_keywords:
- IsGlobal method [.NET Framework metadata]
- IMetaDataImport::IsGlobal method [.NET Framework metadata]
ms.assetid: 44cf6908-f555-4ae8-b2cf-24bd974bf2fe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7032e55d52804d559d1faed810ca7cccd6a9e628
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475635"
---
# <a name="imetadataimportisglobal-method"></a><span data-ttu-id="25b41-102">IMetaDataImport::IsGlobal 方法</span><span class="sxs-lookup"><span data-stu-id="25b41-102">IMetaDataImport::IsGlobal Method</span></span>
<span data-ttu-id="25b41-103">取得一個值，用來表示指定中繼資料語彙基元所代表的欄位、方法或類型值是否具有全域範圍。</span><span class="sxs-lookup"><span data-stu-id="25b41-103">Gets a value indicating whether the field, method, or type represented by the specified metadata token has global scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25b41-104">語法</span><span class="sxs-lookup"><span data-stu-id="25b41-104">Syntax</span></span>  
  
```  
HRESULT IsGlobal (  
   [in]  mdToken     pd,  
   [out] int         *pbGlobal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25b41-105">參數</span><span class="sxs-lookup"><span data-stu-id="25b41-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="25b41-106">[in]中繼資料語彙基元，表示型別、 欄位或方法。</span><span class="sxs-lookup"><span data-stu-id="25b41-106">[in] A metadata token that represents a type, field, or method.</span></span>  
  
 `pbGlobal`  
 <span data-ttu-id="25b41-107">[out] 1，否則此物件會具有全域範圍;否則就是 0 （零）。</span><span class="sxs-lookup"><span data-stu-id="25b41-107">[out] 1 if the object has global scope; otherwise, 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25b41-108">需求</span><span class="sxs-lookup"><span data-stu-id="25b41-108">Requirements</span></span>  
 <span data-ttu-id="25b41-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="25b41-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25b41-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="25b41-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="25b41-111">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="25b41-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="25b41-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25b41-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25b41-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25b41-113">See also</span></span>
- [<span data-ttu-id="25b41-114">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="25b41-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="25b41-115">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="25b41-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
