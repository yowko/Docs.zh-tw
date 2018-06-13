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
ms.openlocfilehash: a7a36d14b67efb3934089dc16de41a3b80ea0c0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447986"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="e7af0-102">IMetaDataTables::GetCodedTokenInfo 方法</span><span class="sxs-lookup"><span data-stu-id="e7af0-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>
<span data-ttu-id="e7af0-103">取得與指定的資料列索引相關聯的語彙基元的陣列指標。</span><span class="sxs-lookup"><span data-stu-id="e7af0-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7af0-104">語法</span><span class="sxs-lookup"><span data-stu-id="e7af0-104">Syntax</span></span>  
  
```  
HRESULT GetCodedTokenInfo (   
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e7af0-105">參數</span><span class="sxs-lookup"><span data-stu-id="e7af0-105">Parameters</span></span>  
 `ixCdTkn`  
 <span data-ttu-id="e7af0-106">[in]自動程式碼傳回的語彙基元種類。</span><span class="sxs-lookup"><span data-stu-id="e7af0-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="e7af0-107">[out]長度指標`ppTokens`。</span><span class="sxs-lookup"><span data-stu-id="e7af0-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="e7af0-108">[out]指向陣列，其中包含傳回的語彙基元清單的指標。</span><span class="sxs-lookup"><span data-stu-id="e7af0-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="e7af0-109">[out]指標的指標為在語彙基元名稱`ixCdTkn`。</span><span class="sxs-lookup"><span data-stu-id="e7af0-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7af0-110">需求</span><span class="sxs-lookup"><span data-stu-id="e7af0-110">Requirements</span></span>  
 <span data-ttu-id="e7af0-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e7af0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7af0-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e7af0-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e7af0-113">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e7af0-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e7af0-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7af0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7af0-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7af0-115">See Also</span></span>  
 [<span data-ttu-id="e7af0-116">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="e7af0-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="e7af0-117">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="e7af0-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
