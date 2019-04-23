---
title: IMetaDataEmit::DefineUserString 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineUserString
helpviewer_keywords:
- DefineUserString method [.NET Framework metadata]
- IMetaDataEmit::DefineUserString method [.NET Framework metadata]
ms.assetid: 88fb7ef3-bbdf-429c-b678-c9c153456461
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f24dd3864be1bda454ac5e863f3fa2caf736bda9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59215218"
---
# <a name="imetadataemitdefineuserstring-method"></a><span data-ttu-id="7d387-102">IMetaDataEmit::DefineUserString 方法</span><span class="sxs-lookup"><span data-stu-id="7d387-102">IMetaDataEmit::DefineUserString Method</span></span>
<span data-ttu-id="7d387-103">取得指定的常值字串的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="7d387-103">Gets a metadata token for the specified literal string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d387-104">語法</span><span class="sxs-lookup"><span data-stu-id="7d387-104">Syntax</span></span>  
  
```  
HRESULT DefineUserString (   
    [in]  LPCWSTR     szString,   
    [in]  ULONG       cchString,   
    [out] mdString    *pstk   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d387-105">參數</span><span class="sxs-lookup"><span data-stu-id="7d387-105">Parameters</span></span>  
 `szString`  
 <span data-ttu-id="7d387-106">[in]要儲存的使用者字串。</span><span class="sxs-lookup"><span data-stu-id="7d387-106">[in] The user string to store.</span></span>  
  
 `cchString`  
 <span data-ttu-id="7d387-107">[in]中的寬字元的計數`szString`。</span><span class="sxs-lookup"><span data-stu-id="7d387-107">[in] The count of wide characters in `szString`.</span></span>  
  
 `pstk`  
 <span data-ttu-id="7d387-108">[out]指派的字串權杖。</span><span class="sxs-lookup"><span data-stu-id="7d387-108">[out] The string token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d387-109">需求</span><span class="sxs-lookup"><span data-stu-id="7d387-109">Requirements</span></span>  
 <span data-ttu-id="7d387-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7d387-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d387-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7d387-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7d387-112">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7d387-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d387-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d387-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d387-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d387-114">See also</span></span>

- [<span data-ttu-id="7d387-115">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="7d387-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="7d387-116">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="7d387-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
