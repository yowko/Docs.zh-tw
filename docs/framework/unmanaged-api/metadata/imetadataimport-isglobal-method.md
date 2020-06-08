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
ms.openlocfilehash: d477976952d2c1875a620d1397fd43e5c5e2836f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503467"
---
# <a name="imetadataimportisglobal-method"></a><span data-ttu-id="53c5d-102">IMetaDataImport::IsGlobal 方法</span><span class="sxs-lookup"><span data-stu-id="53c5d-102">IMetaDataImport::IsGlobal Method</span></span>
<span data-ttu-id="53c5d-103">取得一個值，用來表示指定中繼資料語彙基元所代表的欄位、方法或類型值是否具有全域範圍。</span><span class="sxs-lookup"><span data-stu-id="53c5d-103">Gets a value indicating whether the field, method, or type represented by the specified metadata token has global scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53c5d-104">語法</span><span class="sxs-lookup"><span data-stu-id="53c5d-104">Syntax</span></span>  
  
```cpp  
HRESULT IsGlobal (  
   [in]  mdToken     pd,  
   [out] int         *pbGlobal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53c5d-105">參數</span><span class="sxs-lookup"><span data-stu-id="53c5d-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="53c5d-106">在代表類型、欄位或方法的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="53c5d-106">[in] A metadata token that represents a type, field, or method.</span></span>  
  
 `pbGlobal`  
 <span data-ttu-id="53c5d-107">[out] 1，如果物件具有全域範圍，則為，否則為0（零）。</span><span class="sxs-lookup"><span data-stu-id="53c5d-107">[out] 1 if the object has global scope; otherwise, 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53c5d-108">規格需求</span><span class="sxs-lookup"><span data-stu-id="53c5d-108">Requirements</span></span>  
 <span data-ttu-id="53c5d-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="53c5d-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53c5d-110">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="53c5d-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="53c5d-111">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="53c5d-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="53c5d-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53c5d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53c5d-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53c5d-113">See also</span></span>

- [<span data-ttu-id="53c5d-114">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="53c5d-114">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="53c5d-115">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="53c5d-115">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
