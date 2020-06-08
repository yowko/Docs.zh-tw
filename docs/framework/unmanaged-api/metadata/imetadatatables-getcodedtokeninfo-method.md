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
ms.openlocfilehash: 8ab16ad5b2b2838125e07511ef47be737f40671c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501205"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="03db0-102">IMetaDataTables::GetCodedTokenInfo 方法</span><span class="sxs-lookup"><span data-stu-id="03db0-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>
<span data-ttu-id="03db0-103">取得與指定之資料列索引相關聯之標記陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="03db0-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03db0-104">語法</span><span class="sxs-lookup"><span data-stu-id="03db0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodedTokenInfo (
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03db0-105">參數</span><span class="sxs-lookup"><span data-stu-id="03db0-105">Parameters</span></span>  
 `ixCdTkn`  
 <span data-ttu-id="03db0-106">在要傳回之編碼 token 的種類。</span><span class="sxs-lookup"><span data-stu-id="03db0-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="03db0-107">脫銷長度的指標 `ppTokens` 。</span><span class="sxs-lookup"><span data-stu-id="03db0-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="03db0-108">脫銷陣列指標的指標，其中包含傳回之標記的清單。</span><span class="sxs-lookup"><span data-stu-id="03db0-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="03db0-109">脫銷指向之標記名稱的指標 `ixCdTkn` 。</span><span class="sxs-lookup"><span data-stu-id="03db0-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03db0-110">規格需求</span><span class="sxs-lookup"><span data-stu-id="03db0-110">Requirements</span></span>  
 <span data-ttu-id="03db0-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="03db0-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03db0-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="03db0-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="03db0-113">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="03db0-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="03db0-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03db0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03db0-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03db0-115">See also</span></span>

- [<span data-ttu-id="03db0-116">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="03db0-116">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="03db0-117">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="03db0-117">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
