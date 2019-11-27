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
ms.openlocfilehash: 577a4f6bb8315cfb1cb462703dd0cb9b23b60704
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434063"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="47645-102">IMetaDataTables::GetCodedTokenInfo 方法</span><span class="sxs-lookup"><span data-stu-id="47645-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>
<span data-ttu-id="47645-103">取得與指定之資料列索引相關聯之標記陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="47645-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47645-104">語法</span><span class="sxs-lookup"><span data-stu-id="47645-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodedTokenInfo (   
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47645-105">參數</span><span class="sxs-lookup"><span data-stu-id="47645-105">Parameters</span></span>  
 `ixCdTkn`  
 <span data-ttu-id="47645-106">在要傳回之編碼 token 的種類。</span><span class="sxs-lookup"><span data-stu-id="47645-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="47645-107">脫銷`ppTokens`長度的指標。</span><span class="sxs-lookup"><span data-stu-id="47645-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="47645-108">脫銷陣列指標的指標，其中包含傳回之標記的清單。</span><span class="sxs-lookup"><span data-stu-id="47645-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="47645-109">脫銷在 `ixCdTkn`之 token 名稱指標的指標。</span><span class="sxs-lookup"><span data-stu-id="47645-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47645-110">需求</span><span class="sxs-lookup"><span data-stu-id="47645-110">Requirements</span></span>  
 <span data-ttu-id="47645-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="47645-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47645-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="47645-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="47645-113">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="47645-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="47645-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47645-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47645-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47645-115">See also</span></span>

- [<span data-ttu-id="47645-116">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="47645-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="47645-117">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="47645-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
