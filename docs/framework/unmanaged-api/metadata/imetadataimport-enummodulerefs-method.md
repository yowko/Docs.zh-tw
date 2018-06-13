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
ms.openlocfilehash: 294156983507476b7ddfda3bc3cad16bb32f422b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445405"
---
# <a name="imetadataimportenummodulerefs-method"></a><span data-ttu-id="7e7ea-102">IMetaDataImport::EnumModuleRefs 方法</span><span class="sxs-lookup"><span data-stu-id="7e7ea-102">IMetaDataImport::EnumModuleRefs Method</span></span>
<span data-ttu-id="7e7ea-103">列舉代表已匯入的模組之 ModuleRef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="7e7ea-103">Enumerates ModuleRef tokens that represent imported modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e7ea-104">語法</span><span class="sxs-lookup"><span data-stu-id="7e7ea-104">Syntax</span></span>  
  
```  
HRESULT EnumModuleRefs (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdModuleRef  rModuleRefs[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcModuleRefs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7e7ea-105">參數</span><span class="sxs-lookup"><span data-stu-id="7e7ea-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="7e7ea-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="7e7ea-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="7e7ea-107">這必須是 NULL 的第一個呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="7e7ea-107">This must be NULL for the first call of this method.</span></span>  
  
 `rModuleRefs`  
 <span data-ttu-id="7e7ea-108">[out]陣列，用來儲存 ModuleRef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="7e7ea-108">[out] The array used to store the ModuleRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="7e7ea-109">[in] `rModuleRefs` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="7e7ea-109">[in] The maximum size of the `rModuleRefs` array.</span></span>  
  
 `pcModuleRefs`  
 <span data-ttu-id="7e7ea-110">[out]ModuleRef 語彙基元中傳回的數目`rModuleRefs`。</span><span class="sxs-lookup"><span data-stu-id="7e7ea-110">[out] The number of ModuleRef tokens returned in `rModuleRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7e7ea-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="7e7ea-111">Return Value</span></span>  
  
|<span data-ttu-id="7e7ea-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7e7ea-112">HRESULT</span></span>|<span data-ttu-id="7e7ea-113">描述</span><span class="sxs-lookup"><span data-stu-id="7e7ea-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="7e7ea-114">`EnumModuleRefs` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="7e7ea-114">`EnumModuleRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="7e7ea-115">沒有列舉語彙基元。</span><span class="sxs-lookup"><span data-stu-id="7e7ea-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="7e7ea-116">在此情況下，`pcModuleRefs`為零。</span><span class="sxs-lookup"><span data-stu-id="7e7ea-116">In that case, `pcModuleRefs` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7e7ea-117">需求</span><span class="sxs-lookup"><span data-stu-id="7e7ea-117">Requirements</span></span>  
 <span data-ttu-id="7e7ea-118">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7e7ea-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e7ea-119">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7e7ea-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7e7ea-120">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7e7ea-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7e7ea-121">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e7ea-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e7ea-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e7ea-122">See Also</span></span>  
 [<span data-ttu-id="7e7ea-123">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="7e7ea-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="7e7ea-124">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="7e7ea-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
