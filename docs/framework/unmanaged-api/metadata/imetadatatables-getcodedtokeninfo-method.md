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
ms.openlocfilehash: 153aa7d6b8c35129638de3d47ffa6aff72f550c9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946762"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="2594f-102">IMetaDataTables::GetCodedTokenInfo 方法</span><span class="sxs-lookup"><span data-stu-id="2594f-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>
<span data-ttu-id="2594f-103">取得與指定的資料列索引相關聯的語彙基元的陣列指標。</span><span class="sxs-lookup"><span data-stu-id="2594f-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2594f-104">語法</span><span class="sxs-lookup"><span data-stu-id="2594f-104">Syntax</span></span>  
  
```  
HRESULT GetCodedTokenInfo (   
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2594f-105">參數</span><span class="sxs-lookup"><span data-stu-id="2594f-105">Parameters</span></span>  
 `ixCdTkn`  
 <span data-ttu-id="2594f-106">[in]要傳回的自動程式化語彙基元種類。</span><span class="sxs-lookup"><span data-stu-id="2594f-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="2594f-107">[out]長度指標`ppTokens`。</span><span class="sxs-lookup"><span data-stu-id="2594f-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="2594f-108">[out]陣列，其中包含清單的指標的指標傳回權杖。</span><span class="sxs-lookup"><span data-stu-id="2594f-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="2594f-109">[out]在語彙基元名稱的指標的指標`ixCdTkn`。</span><span class="sxs-lookup"><span data-stu-id="2594f-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2594f-110">需求</span><span class="sxs-lookup"><span data-stu-id="2594f-110">Requirements</span></span>  
 <span data-ttu-id="2594f-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2594f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2594f-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2594f-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2594f-113">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2594f-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2594f-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2594f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2594f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2594f-115">See also</span></span>

- [<span data-ttu-id="2594f-116">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="2594f-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="2594f-117">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="2594f-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
