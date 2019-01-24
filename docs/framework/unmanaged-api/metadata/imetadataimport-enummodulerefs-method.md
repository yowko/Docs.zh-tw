---
title: IMetaDataImport::EnumModuleRefs 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumModuleRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumModuleRefs
helpviewer_keywords:
- EnumModuleRefs method [.NET Framework metadata]
- IMetaDataImport::EnumModuleRefs method [.NET Framework metadata]
ms.assetid: 53441f3a-68d2-477c-906e-37c55dfcfb4d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e84581a0642fe5bee3b88b6774ab2155fd2736a0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54490780"
---
# <a name="imetadataimportenummodulerefs-method"></a><span data-ttu-id="44d9b-102">IMetaDataImport::EnumModuleRefs 方法</span><span class="sxs-lookup"><span data-stu-id="44d9b-102">IMetaDataImport::EnumModuleRefs Method</span></span>
<span data-ttu-id="44d9b-103">列舉代表已匯入的模組之 ModuleRef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="44d9b-103">Enumerates ModuleRef tokens that represent imported modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44d9b-104">語法</span><span class="sxs-lookup"><span data-stu-id="44d9b-104">Syntax</span></span>  
  
```  
HRESULT EnumModuleRefs (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdModuleRef  rModuleRefs[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcModuleRefs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="44d9b-105">參數</span><span class="sxs-lookup"><span data-stu-id="44d9b-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="44d9b-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="44d9b-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="44d9b-107">首次呼叫這個方法，這必須是 NULL。</span><span class="sxs-lookup"><span data-stu-id="44d9b-107">This must be NULL for the first call of this method.</span></span>  
  
 `rModuleRefs`  
 <span data-ttu-id="44d9b-108">[out]陣列，用來儲存 ModuleRef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="44d9b-108">[out] The array used to store the ModuleRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="44d9b-109">[in] `rModuleRefs` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="44d9b-109">[in] The maximum size of the `rModuleRefs` array.</span></span>  
  
 `pcModuleRefs`  
 <span data-ttu-id="44d9b-110">[out]ModuleRef 語彙基元中傳回的數目`rModuleRefs`。</span><span class="sxs-lookup"><span data-stu-id="44d9b-110">[out] The number of ModuleRef tokens returned in `rModuleRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44d9b-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="44d9b-111">Return Value</span></span>  
  
|<span data-ttu-id="44d9b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="44d9b-112">HRESULT</span></span>|<span data-ttu-id="44d9b-113">描述</span><span class="sxs-lookup"><span data-stu-id="44d9b-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="44d9b-114">`EnumModuleRefs` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="44d9b-114">`EnumModuleRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="44d9b-115">沒有列舉語彙基元。</span><span class="sxs-lookup"><span data-stu-id="44d9b-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="44d9b-116">在此情況下，`pcModuleRefs`為零。</span><span class="sxs-lookup"><span data-stu-id="44d9b-116">In that case, `pcModuleRefs` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="44d9b-117">需求</span><span class="sxs-lookup"><span data-stu-id="44d9b-117">Requirements</span></span>  
 <span data-ttu-id="44d9b-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="44d9b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44d9b-119">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="44d9b-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="44d9b-120">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="44d9b-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="44d9b-121">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44d9b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44d9b-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44d9b-122">See also</span></span>
- [<span data-ttu-id="44d9b-123">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="44d9b-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="44d9b-124">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="44d9b-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
