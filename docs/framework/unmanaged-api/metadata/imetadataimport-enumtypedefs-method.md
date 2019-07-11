---
title: IMetaDataImport::EnumTypeDefs 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeDefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 621582536c07b269dd723c9014e23c50e561957a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774609"
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="f1dcb-102">IMetaDataImport::EnumTypeDefs 方法</span><span class="sxs-lookup"><span data-stu-id="f1dcb-102">IMetaDataImport::EnumTypeDefs Method</span></span>
<span data-ttu-id="f1dcb-103">列舉代表目前範圍內的所有類型的 TypeDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="f1dcb-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1dcb-104">語法</span><span class="sxs-lookup"><span data-stu-id="f1dcb-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,   
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,   
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1dcb-105">參數</span><span class="sxs-lookup"><span data-stu-id="f1dcb-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="f1dcb-106">[out]新的列舉值指標。</span><span class="sxs-lookup"><span data-stu-id="f1dcb-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="f1dcb-107">首次呼叫這個方法，這必須是 NULL。</span><span class="sxs-lookup"><span data-stu-id="f1dcb-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="f1dcb-108">[in]陣列，用來儲存的 TypeDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="f1dcb-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f1dcb-109">[in] `rTypeDefs` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="f1dcb-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="f1dcb-110">[out]中傳回的 TypeDef 語彙基元數目`rTypeDefs`。</span><span class="sxs-lookup"><span data-stu-id="f1dcb-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1dcb-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="f1dcb-111">Return Value</span></span>  
  
|<span data-ttu-id="f1dcb-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f1dcb-112">HRESULT</span></span>|<span data-ttu-id="f1dcb-113">說明</span><span class="sxs-lookup"><span data-stu-id="f1dcb-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f1dcb-114">`EnumTypeDefs` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="f1dcb-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f1dcb-115">沒有列舉語彙基元。</span><span class="sxs-lookup"><span data-stu-id="f1dcb-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="f1dcb-116">在此情況下，`pcTypeDefs`為零。</span><span class="sxs-lookup"><span data-stu-id="f1dcb-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1dcb-117">備註</span><span class="sxs-lookup"><span data-stu-id="f1dcb-117">Remarks</span></span>  
 <span data-ttu-id="f1dcb-118">TypeDef 語彙基元所代表的類型，例如類別或介面，以及透過擴充性機制新增任何型別。</span><span class="sxs-lookup"><span data-stu-id="f1dcb-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1dcb-119">需求</span><span class="sxs-lookup"><span data-stu-id="f1dcb-119">Requirements</span></span>  
 <span data-ttu-id="f1dcb-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f1dcb-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1dcb-121">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f1dcb-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f1dcb-122">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f1dcb-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f1dcb-123">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1dcb-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1dcb-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1dcb-124">See also</span></span>

- [<span data-ttu-id="f1dcb-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="f1dcb-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="f1dcb-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="f1dcb-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
