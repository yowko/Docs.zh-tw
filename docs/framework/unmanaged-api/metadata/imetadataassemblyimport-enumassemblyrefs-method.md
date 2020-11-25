---
title: IMetaDataAssemblyImport::EnumAssemblyRefs 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumAssemblyRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs method [.NET Framework metadata]
- EnumAssemblyRefs method [.NET Framework metadata]
ms.assetid: 8844d0dd-730e-4592-8a7b-c1462d312c70
topic_type:
- apiref
ms.openlocfilehash: 18cd9dd14e615a7e76bfff30c9ae584305bd1907
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708927"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="96925-102">IMetaDataAssemblyImport::EnumAssemblyRefs 方法</span><span class="sxs-lookup"><span data-stu-id="96925-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>

<span data-ttu-id="96925-103">列舉 `mdAssemblyRef` 組件資訊清單中所定義的實例。</span><span class="sxs-lookup"><span data-stu-id="96925-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96925-104">語法</span><span class="sxs-lookup"><span data-stu-id="96925-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,
    [out]     mdAssemblyRef   rAssemblyRefs[],
    [in]      ULONG           cMax,
    [out]     ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96925-105">參數</span><span class="sxs-lookup"><span data-stu-id="96925-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="96925-106">[in，out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="96925-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="96925-107">第一次呼叫方法時，此值必須為 null 值 `EnumAssemblyRefs` 。</span><span class="sxs-lookup"><span data-stu-id="96925-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="96925-108">擴展 `mdAssemblyRef` 元資料標記的列舉。</span><span class="sxs-lookup"><span data-stu-id="96925-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="96925-109">在可放置在陣列中的最大 token 數目 `rAssemblyRefs` 。</span><span class="sxs-lookup"><span data-stu-id="96925-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="96925-110">擴展實際放置的權杖數目 `rAssemblyRefs` 。</span><span class="sxs-lookup"><span data-stu-id="96925-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96925-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="96925-111">Return Value</span></span>  
  
|<span data-ttu-id="96925-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="96925-112">HRESULT</span></span>|<span data-ttu-id="96925-113">描述</span><span class="sxs-lookup"><span data-stu-id="96925-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="96925-114">`EnumAssemblyRefs` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="96925-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="96925-115">沒有要列舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="96925-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="96925-116">在此情況下， `pcTokens` 會設定為零。</span><span class="sxs-lookup"><span data-stu-id="96925-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="96925-117">需求</span><span class="sxs-lookup"><span data-stu-id="96925-117">Requirements</span></span>  

 <span data-ttu-id="96925-118">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="96925-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96925-119">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="96925-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="96925-120">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="96925-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="96925-121">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96925-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96925-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96925-122">See also</span></span>

- [<span data-ttu-id="96925-123">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="96925-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
