---
title: IMetaDataAssemblyImport::EnumFiles 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumFiles
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumFiles
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumFiles method [.NET Framework metadata]
- EnumFiles method [.NET Framework metadata]
ms.assetid: f0d721e2-b946-426d-8e20-9124bd04e4cb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5848a14a20b63ffbf806bb56886b75360323b698
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496179"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="1222a-102">IMetaDataAssemblyImport::EnumFiles 方法</span><span class="sxs-lookup"><span data-stu-id="1222a-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>
<span data-ttu-id="1222a-103">列舉在目前的組件資訊清單中所參考的檔案。</span><span class="sxs-lookup"><span data-stu-id="1222a-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1222a-104">語法</span><span class="sxs-lookup"><span data-stu-id="1222a-104">Syntax</span></span>  
  
```  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,   
    [out] mdFile          rFiles[],   
    [in]  ULONG           cMax,   
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1222a-105">參數</span><span class="sxs-lookup"><span data-stu-id="1222a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="1222a-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="1222a-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="1222a-107">這必須是第一次呼叫此方法的 null 值。</span><span class="sxs-lookup"><span data-stu-id="1222a-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="1222a-108">[out]用來儲存陣列`mdFile`中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="1222a-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="1222a-109">[in]最大數目`mdFile`語彙基元可以放入`rFiles`。</span><span class="sxs-lookup"><span data-stu-id="1222a-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="1222a-110">[out]數目`mdFile`語彙基元實際上置於`rFiles`。</span><span class="sxs-lookup"><span data-stu-id="1222a-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1222a-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="1222a-111">Return Value</span></span>  
  
|<span data-ttu-id="1222a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1222a-112">HRESULT</span></span>|<span data-ttu-id="1222a-113">描述</span><span class="sxs-lookup"><span data-stu-id="1222a-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="1222a-114">`EnumFiles` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="1222a-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="1222a-115">沒有列舉語彙基元。</span><span class="sxs-lookup"><span data-stu-id="1222a-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="1222a-116">在此情況下，`pcTokens`設為零。</span><span class="sxs-lookup"><span data-stu-id="1222a-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1222a-117">需求</span><span class="sxs-lookup"><span data-stu-id="1222a-117">Requirements</span></span>  
 <span data-ttu-id="1222a-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1222a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1222a-119">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1222a-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1222a-120">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1222a-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1222a-121">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1222a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1222a-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1222a-122">See also</span></span>
- [<span data-ttu-id="1222a-123">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="1222a-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
