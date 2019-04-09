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
ms.openlocfilehash: 20913d1cfa258036e8c20e826415f96a8984fdb4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103359"
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="f7d06-102">IMetaDataImport::EnumTypeDefs 方法</span><span class="sxs-lookup"><span data-stu-id="f7d06-102">IMetaDataImport::EnumTypeDefs Method</span></span>
<span data-ttu-id="f7d06-103">列舉代表目前範圍內的所有類型的 TypeDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="f7d06-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7d06-104">語法</span><span class="sxs-lookup"><span data-stu-id="f7d06-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,   
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,   
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7d06-105">參數</span><span class="sxs-lookup"><span data-stu-id="f7d06-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="f7d06-106">[out]新的列舉值指標。</span><span class="sxs-lookup"><span data-stu-id="f7d06-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="f7d06-107">首次呼叫這個方法，這必須是 NULL。</span><span class="sxs-lookup"><span data-stu-id="f7d06-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="f7d06-108">[in]陣列，用來儲存的 TypeDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="f7d06-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f7d06-109">[in] `rTypeDefs` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="f7d06-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="f7d06-110">[out]中傳回的 TypeDef 語彙基元數目`rTypeDefs`。</span><span class="sxs-lookup"><span data-stu-id="f7d06-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7d06-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="f7d06-111">Return Value</span></span>  
  
|<span data-ttu-id="f7d06-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f7d06-112">HRESULT</span></span>|<span data-ttu-id="f7d06-113">描述</span><span class="sxs-lookup"><span data-stu-id="f7d06-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumTypeDefs` <span data-ttu-id="f7d06-114">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="f7d06-114">returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f7d06-115">沒有列舉語彙基元。</span><span class="sxs-lookup"><span data-stu-id="f7d06-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="f7d06-116">在此情況下，`pcTypeDefs`為零。</span><span class="sxs-lookup"><span data-stu-id="f7d06-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7d06-117">備註</span><span class="sxs-lookup"><span data-stu-id="f7d06-117">Remarks</span></span>  
 <span data-ttu-id="f7d06-118">TypeDef 語彙基元所代表的類型，例如類別或介面，以及透過擴充性機制新增任何型別。</span><span class="sxs-lookup"><span data-stu-id="f7d06-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7d06-119">需求</span><span class="sxs-lookup"><span data-stu-id="f7d06-119">Requirements</span></span>  
 <span data-ttu-id="f7d06-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f7d06-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7d06-121">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f7d06-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f7d06-122">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f7d06-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="f7d06-123">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="f7d06-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f7d06-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7d06-124">See also</span></span>

- [<span data-ttu-id="f7d06-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="f7d06-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="f7d06-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="f7d06-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
