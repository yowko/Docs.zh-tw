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
ms.openlocfilehash: ed8bafd67b5d55a5116111b7721fbdc31c52aca6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009090"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="d1d7d-102">IMetaDataAssemblyImport::EnumFiles 方法</span><span class="sxs-lookup"><span data-stu-id="d1d7d-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>
<span data-ttu-id="d1d7d-103">列舉目前組件資訊清單中參考的檔案。</span><span class="sxs-lookup"><span data-stu-id="d1d7d-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1d7d-104">語法</span><span class="sxs-lookup"><span data-stu-id="d1d7d-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,
    [out] mdFile          rFiles[],
    [in]  ULONG           cMax,
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1d7d-105">參數</span><span class="sxs-lookup"><span data-stu-id="d1d7d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="d1d7d-106">[in、out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="d1d7d-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="d1d7d-107">此方法的第一次呼叫必須是 null 值。</span><span class="sxs-lookup"><span data-stu-id="d1d7d-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="d1d7d-108">脫銷用來儲存 `mdFile` 元資料標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="d1d7d-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d1d7d-109">在`mdFile`可以放入的標記數目上限 `rFiles` 。</span><span class="sxs-lookup"><span data-stu-id="d1d7d-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="d1d7d-110">脫銷`mdFile`實際放入的權杖數目 `rFiles` 。</span><span class="sxs-lookup"><span data-stu-id="d1d7d-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1d7d-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="d1d7d-111">Return Value</span></span>  
  
|<span data-ttu-id="d1d7d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d1d7d-112">HRESULT</span></span>|<span data-ttu-id="d1d7d-113">描述</span><span class="sxs-lookup"><span data-stu-id="d1d7d-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d1d7d-114">`EnumFiles`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="d1d7d-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d1d7d-115">沒有要列舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="d1d7d-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="d1d7d-116">在此情況下， `pcTokens` 會設定為零。</span><span class="sxs-lookup"><span data-stu-id="d1d7d-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d1d7d-117">需求</span><span class="sxs-lookup"><span data-stu-id="d1d7d-117">Requirements</span></span>  
 <span data-ttu-id="d1d7d-118">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d1d7d-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1d7d-119">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="d1d7d-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d1d7d-120">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="d1d7d-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d1d7d-121">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1d7d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1d7d-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1d7d-122">See also</span></span>

- [<span data-ttu-id="d1d7d-123">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="d1d7d-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
