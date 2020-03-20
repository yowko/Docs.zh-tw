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
ms.openlocfilehash: 64c70fe0b657047ae35dccb763fa57120403deef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177144"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="65793-102">IMetaDataTables::GetCodedTokenInfo 方法</span><span class="sxs-lookup"><span data-stu-id="65793-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>
<span data-ttu-id="65793-103">獲取指向與指定行索引關聯的權杖陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="65793-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65793-104">語法</span><span class="sxs-lookup"><span data-stu-id="65793-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodedTokenInfo (
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65793-105">參數</span><span class="sxs-lookup"><span data-stu-id="65793-105">Parameters</span></span>  
 `ixCdTkn`  
 <span data-ttu-id="65793-106">[在]要返回的編碼權杖類型。</span><span class="sxs-lookup"><span data-stu-id="65793-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="65793-107">[出]指向 長度的`ppTokens`指標。</span><span class="sxs-lookup"><span data-stu-id="65793-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="65793-108">[出]指向包含返回權杖清單的陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="65793-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="65793-109">[出]指向 的`ixCdTkn`標記名稱的指標。</span><span class="sxs-lookup"><span data-stu-id="65793-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65793-110">需求</span><span class="sxs-lookup"><span data-stu-id="65793-110">Requirements</span></span>  
 <span data-ttu-id="65793-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="65793-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65793-112">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="65793-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="65793-113">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="65793-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="65793-114">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65793-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65793-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65793-115">See also</span></span>

- [<span data-ttu-id="65793-116">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="65793-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="65793-117">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="65793-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
