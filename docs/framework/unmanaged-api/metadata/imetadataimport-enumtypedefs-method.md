---
title: "IMetaDataImport::EnumTypeDefs 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumTypeDefs
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aeb0e3c2eab4cde219b050bcf0e50202fe2be3f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="4bed0-102">IMetaDataImport::EnumTypeDefs 方法</span><span class="sxs-lookup"><span data-stu-id="4bed0-102">IMetaDataImport::EnumTypeDefs Method</span></span>
<span data-ttu-id="4bed0-103">列舉代表目前範圍內的所有類型的 TypeDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="4bed0-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bed0-104">語法</span><span class="sxs-lookup"><span data-stu-id="4bed0-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,   
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,   
   [out] ULONG      *pcTypeDefs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4bed0-105">參數</span><span class="sxs-lookup"><span data-stu-id="4bed0-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="4bed0-106">[out]新的列舉值指標。</span><span class="sxs-lookup"><span data-stu-id="4bed0-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="4bed0-107">這必須是 NULL 的第一個呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="4bed0-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="4bed0-108">[in]陣列，用來儲存的 TypeDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="4bed0-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="4bed0-109">[in] `rTypeDefs` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="4bed0-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="4bed0-110">[out]傳回的 TypeDef 語彙基元數目`rTypeDefs`。</span><span class="sxs-lookup"><span data-stu-id="4bed0-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4bed0-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="4bed0-111">Return Value</span></span>  
  
|<span data-ttu-id="4bed0-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4bed0-112">HRESULT</span></span>|<span data-ttu-id="4bed0-113">描述</span><span class="sxs-lookup"><span data-stu-id="4bed0-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="4bed0-114">`EnumTypeDefs`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="4bed0-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="4bed0-115">沒有列舉語彙基元。</span><span class="sxs-lookup"><span data-stu-id="4bed0-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="4bed0-116">在此情況下，`pcTypeDefs`為零。</span><span class="sxs-lookup"><span data-stu-id="4bed0-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4bed0-117">備註</span><span class="sxs-lookup"><span data-stu-id="4bed0-117">Remarks</span></span>  
 <span data-ttu-id="4bed0-118">TypeDef 語彙基元所代表的類型，例如類別或介面，以及透過 擴充性機制加入任何型別。</span><span class="sxs-lookup"><span data-stu-id="4bed0-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bed0-119">需求</span><span class="sxs-lookup"><span data-stu-id="4bed0-119">Requirements</span></span>  
 <span data-ttu-id="4bed0-120">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4bed0-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bed0-121">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4bed0-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4bed0-122">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4bed0-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4bed0-123">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bed0-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bed0-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="4bed0-124">See Also</span></span>  
 [<span data-ttu-id="4bed0-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="4bed0-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="4bed0-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="4bed0-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
