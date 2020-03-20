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
ms.openlocfilehash: 70f76318f51047cb81262f744a6fbed5fe401692
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177808"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="cc1da-102">IMetaDataAssemblyImport::EnumFiles 方法</span><span class="sxs-lookup"><span data-stu-id="cc1da-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>
<span data-ttu-id="cc1da-103">枚舉當前組件資訊清單中引用的檔。</span><span class="sxs-lookup"><span data-stu-id="cc1da-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc1da-104">語法</span><span class="sxs-lookup"><span data-stu-id="cc1da-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,
    [out] mdFile          rFiles[],
    [in]  ULONG           cMax,
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc1da-105">參數</span><span class="sxs-lookup"><span data-stu-id="cc1da-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="cc1da-106">[進出]指向枚舉器的指標。</span><span class="sxs-lookup"><span data-stu-id="cc1da-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="cc1da-107">對於此方法的第一個調用，這必須是 null 值。</span><span class="sxs-lookup"><span data-stu-id="cc1da-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="cc1da-108">[出]用於存儲中繼資料權杖的`mdFile`陣列。</span><span class="sxs-lookup"><span data-stu-id="cc1da-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="cc1da-109">[在]可放置在 中`mdFile`的最大權杖數`rFiles`。</span><span class="sxs-lookup"><span data-stu-id="cc1da-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="cc1da-110">[出]實際放置在`mdFile`中的`rFiles`權杖數。</span><span class="sxs-lookup"><span data-stu-id="cc1da-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cc1da-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="cc1da-111">Return Value</span></span>  
  
|<span data-ttu-id="cc1da-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cc1da-112">HRESULT</span></span>|<span data-ttu-id="cc1da-113">描述</span><span class="sxs-lookup"><span data-stu-id="cc1da-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="cc1da-114">`EnumFiles`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="cc1da-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="cc1da-115">沒有要枚舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="cc1da-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="cc1da-116">在這種情況下，`pcTokens`設置為零。</span><span class="sxs-lookup"><span data-stu-id="cc1da-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cc1da-117">需求</span><span class="sxs-lookup"><span data-stu-id="cc1da-117">Requirements</span></span>  
 <span data-ttu-id="cc1da-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cc1da-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc1da-119">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="cc1da-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cc1da-120">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="cc1da-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cc1da-121">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc1da-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc1da-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc1da-122">See also</span></span>

- [<span data-ttu-id="cc1da-123">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="cc1da-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
