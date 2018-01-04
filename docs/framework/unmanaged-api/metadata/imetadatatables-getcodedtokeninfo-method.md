---
title: "IMetaDataTables::GetCodedTokenInfo 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetCodedTokenInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetCodedTokenInfo
helpviewer_keywords:
- GetCodedTokenInfo method [.NET Framework metadata]
- IMetaDataTables::GetCodedTokenInfo method [.NET Framework metadata]
ms.assetid: 31214d3a-715e-49af-92b3-0fd11e4f218a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72c88751940da16a691a5eae46507986a50904a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="f8cba-102">IMetaDataTables::GetCodedTokenInfo 方法</span><span class="sxs-lookup"><span data-stu-id="f8cba-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>
<span data-ttu-id="f8cba-103">取得與指定的資料列索引相關聯的語彙基元的陣列指標。</span><span class="sxs-lookup"><span data-stu-id="f8cba-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8cba-104">語法</span><span class="sxs-lookup"><span data-stu-id="f8cba-104">Syntax</span></span>  
  
```  
HRESULT GetCodedTokenInfo (   
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f8cba-105">參數</span><span class="sxs-lookup"><span data-stu-id="f8cba-105">Parameters</span></span>  
 `ixCdTkn`  
 <span data-ttu-id="f8cba-106">[in]自動程式碼傳回的語彙基元種類。</span><span class="sxs-lookup"><span data-stu-id="f8cba-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="f8cba-107">[out]長度指標`ppTokens`。</span><span class="sxs-lookup"><span data-stu-id="f8cba-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="f8cba-108">[out]指向陣列，其中包含傳回的語彙基元清單的指標。</span><span class="sxs-lookup"><span data-stu-id="f8cba-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="f8cba-109">[out]指標的指標為在語彙基元名稱`ixCdTkn`。</span><span class="sxs-lookup"><span data-stu-id="f8cba-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8cba-110">需求</span><span class="sxs-lookup"><span data-stu-id="f8cba-110">Requirements</span></span>  
 <span data-ttu-id="f8cba-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f8cba-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8cba-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f8cba-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f8cba-113">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f8cba-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f8cba-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8cba-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8cba-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="f8cba-115">See Also</span></span>  
 [<span data-ttu-id="f8cba-116">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="f8cba-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="f8cba-117">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="f8cba-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
