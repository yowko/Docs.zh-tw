---
title: "IMetaDataEmit::DefineUserString 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineUserString
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineUserString
helpviewer_keywords:
- DefineUserString method [.NET Framework metadata]
- IMetaDataEmit::DefineUserString method [.NET Framework metadata]
ms.assetid: 88fb7ef3-bbdf-429c-b678-c9c153456461
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: eb3e21e88da8fec08acf1ecbe451c5914b6cccaf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefineuserstring-method"></a><span data-ttu-id="c5e24-102">IMetaDataEmit::DefineUserString 方法</span><span class="sxs-lookup"><span data-stu-id="c5e24-102">IMetaDataEmit::DefineUserString Method</span></span>
<span data-ttu-id="c5e24-103">取得指定的常值字串的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="c5e24-103">Gets a metadata token for the specified literal string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5e24-104">語法</span><span class="sxs-lookup"><span data-stu-id="c5e24-104">Syntax</span></span>  
  
```  
HRESULT DefineUserString (   
    [in]  LPCWSTR     szString,   
    [in]  ULONG       cchString,   
    [out] mdString    *pstk   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5e24-105">參數</span><span class="sxs-lookup"><span data-stu-id="c5e24-105">Parameters</span></span>  
 `szString`  
 <span data-ttu-id="c5e24-106">[in]要儲存的使用者字串。</span><span class="sxs-lookup"><span data-stu-id="c5e24-106">[in] The user string to store.</span></span>  
  
 `cchString`  
 <span data-ttu-id="c5e24-107">[in]中的寬字元的計數`szString`。</span><span class="sxs-lookup"><span data-stu-id="c5e24-107">[in] The count of wide characters in `szString`.</span></span>  
  
 `pstk`  
 <span data-ttu-id="c5e24-108">[out]指派給字串語彙基元。</span><span class="sxs-lookup"><span data-stu-id="c5e24-108">[out] The string token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5e24-109">需求</span><span class="sxs-lookup"><span data-stu-id="c5e24-109">Requirements</span></span>  
 <span data-ttu-id="c5e24-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c5e24-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5e24-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c5e24-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c5e24-112">**程式庫：**做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c5e24-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5e24-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5e24-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5e24-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5e24-114">See Also</span></span>  
 [<span data-ttu-id="c5e24-115">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="c5e24-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="c5e24-116">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="c5e24-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
