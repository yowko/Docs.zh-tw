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
ms.openlocfilehash: 788fd1815415bf8bcfa20d431a5451679d2025bd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728273"
---
# <a name="imetadataimportenummodulerefs-method"></a><span data-ttu-id="4dc97-102">IMetaDataImport::EnumModuleRefs 方法</span><span class="sxs-lookup"><span data-stu-id="4dc97-102">IMetaDataImport::EnumModuleRefs Method</span></span>

<span data-ttu-id="4dc97-103">列舉代表已匯入的模組之 ModuleRef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="4dc97-103">Enumerates ModuleRef tokens that represent imported modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dc97-104">語法</span><span class="sxs-lookup"><span data-stu-id="4dc97-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModuleRefs (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdModuleRef  rModuleRefs[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcModuleRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4dc97-105">參數</span><span class="sxs-lookup"><span data-stu-id="4dc97-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="4dc97-106">[in，out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="4dc97-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="4dc97-107">此方法的第一個呼叫必須是 Null。</span><span class="sxs-lookup"><span data-stu-id="4dc97-107">This must be NULL for the first call of this method.</span></span>  
  
 `rModuleRefs`  
 <span data-ttu-id="4dc97-108">擴展用來儲存 ModuleRef 標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="4dc97-108">[out] The array used to store the ModuleRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="4dc97-109">[in] `rModuleRefs` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="4dc97-109">[in] The maximum size of the `rModuleRefs` array.</span></span>  
  
 `pcModuleRefs`  
 <span data-ttu-id="4dc97-110">擴展傳回的 ModuleRef 權杖數目 `rModuleRefs` 。</span><span class="sxs-lookup"><span data-stu-id="4dc97-110">[out] The number of ModuleRef tokens returned in `rModuleRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4dc97-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="4dc97-111">Return Value</span></span>  
  
|<span data-ttu-id="4dc97-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4dc97-112">HRESULT</span></span>|<span data-ttu-id="4dc97-113">描述</span><span class="sxs-lookup"><span data-stu-id="4dc97-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="4dc97-114">`EnumModuleRefs` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="4dc97-114">`EnumModuleRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="4dc97-115">沒有要列舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="4dc97-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="4dc97-116">在此情況下， `pcModuleRefs` 是零。</span><span class="sxs-lookup"><span data-stu-id="4dc97-116">In that case, `pcModuleRefs` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4dc97-117">需求</span><span class="sxs-lookup"><span data-stu-id="4dc97-117">Requirements</span></span>  

 <span data-ttu-id="4dc97-118">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4dc97-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4dc97-119">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="4dc97-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4dc97-120">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="4dc97-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4dc97-121">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4dc97-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dc97-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4dc97-122">See also</span></span>

- [<span data-ttu-id="4dc97-123">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="4dc97-123">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="4dc97-124">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="4dc97-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
