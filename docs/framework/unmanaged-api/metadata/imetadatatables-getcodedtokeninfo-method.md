---
title: IMetaDataTables::GetCodedTokenInfo 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetCodedTokenInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetCodedTokenInfo
helpviewer_keywords:
- GetCodedTokenInfo method [.NET Framework metadata]
- IMetaDataTables::GetCodedTokenInfo method [.NET Framework metadata]
ms.assetid: 31214d3a-715e-49af-92b3-0fd11e4f218a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11ab93e9cb4449ab77e5e9c4da81073aaf432382
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54669688"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="bb3de-102">IMetaDataTables::GetCodedTokenInfo 方法</span><span class="sxs-lookup"><span data-stu-id="bb3de-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>
<span data-ttu-id="bb3de-103">取得與指定的資料列索引相關聯的語彙基元的陣列指標。</span><span class="sxs-lookup"><span data-stu-id="bb3de-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb3de-104">語法</span><span class="sxs-lookup"><span data-stu-id="bb3de-104">Syntax</span></span>  
  
```  
HRESULT GetCodedTokenInfo (   
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bb3de-105">參數</span><span class="sxs-lookup"><span data-stu-id="bb3de-105">Parameters</span></span>  
 `ixCdTkn`  
 <span data-ttu-id="bb3de-106">[in]要傳回的自動程式化語彙基元種類。</span><span class="sxs-lookup"><span data-stu-id="bb3de-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="bb3de-107">[out]長度指標`ppTokens`。</span><span class="sxs-lookup"><span data-stu-id="bb3de-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="bb3de-108">[out]陣列，其中包含清單的指標的指標傳回權杖。</span><span class="sxs-lookup"><span data-stu-id="bb3de-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="bb3de-109">[out]在語彙基元名稱的指標的指標`ixCdTkn`。</span><span class="sxs-lookup"><span data-stu-id="bb3de-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb3de-110">需求</span><span class="sxs-lookup"><span data-stu-id="bb3de-110">Requirements</span></span>  
 <span data-ttu-id="bb3de-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bb3de-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb3de-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bb3de-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bb3de-113">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="bb3de-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bb3de-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb3de-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb3de-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb3de-115">See also</span></span>
- [<span data-ttu-id="bb3de-116">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="bb3de-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="bb3de-117">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="bb3de-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
