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
ms.openlocfilehash: e4549789ea1af584c0850a535d9f6bb54f844ce0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443553"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="ec97b-102">IMetaDataAssemblyImport::EnumFiles 方法</span><span class="sxs-lookup"><span data-stu-id="ec97b-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>
<span data-ttu-id="ec97b-103">列舉目前組件資訊清單中參考的檔案。</span><span class="sxs-lookup"><span data-stu-id="ec97b-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec97b-104">語法</span><span class="sxs-lookup"><span data-stu-id="ec97b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,   
    [out] mdFile          rFiles[],   
    [in]  ULONG           cMax,   
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec97b-105">參數</span><span class="sxs-lookup"><span data-stu-id="ec97b-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="ec97b-106">[in、out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="ec97b-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="ec97b-107">此方法的第一次呼叫必須是 null 值。</span><span class="sxs-lookup"><span data-stu-id="ec97b-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="ec97b-108">脫銷用來儲存 `mdFile` 元資料標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="ec97b-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ec97b-109">在可以放在 `rFiles`中的 `mdFile` token 的數目上限。</span><span class="sxs-lookup"><span data-stu-id="ec97b-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="ec97b-110">脫銷實際放入 `rFiles`的 `mdFile` token 數目。</span><span class="sxs-lookup"><span data-stu-id="ec97b-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ec97b-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="ec97b-111">Return Value</span></span>  
  
|<span data-ttu-id="ec97b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ec97b-112">HRESULT</span></span>|<span data-ttu-id="ec97b-113">描述</span><span class="sxs-lookup"><span data-stu-id="ec97b-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="ec97b-114">已成功傳回 `EnumFiles`。</span><span class="sxs-lookup"><span data-stu-id="ec97b-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="ec97b-115">沒有要列舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="ec97b-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="ec97b-116">在此情況下，`pcTokens` 會設定為零。</span><span class="sxs-lookup"><span data-stu-id="ec97b-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ec97b-117">需求</span><span class="sxs-lookup"><span data-stu-id="ec97b-117">Requirements</span></span>  
 <span data-ttu-id="ec97b-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ec97b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec97b-119">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="ec97b-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ec97b-120">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="ec97b-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ec97b-121">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec97b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec97b-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec97b-122">See also</span></span>

- [<span data-ttu-id="ec97b-123">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="ec97b-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
