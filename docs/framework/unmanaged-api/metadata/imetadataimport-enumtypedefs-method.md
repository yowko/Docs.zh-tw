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
ms.openlocfilehash: a07d9ff237e6d3838fffb068e3a9ebf9febf66fc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="2b17a-102">IMetaDataImport::EnumTypeDefs 方法</span><span class="sxs-lookup"><span data-stu-id="2b17a-102">IMetaDataImport::EnumTypeDefs Method</span></span>
<span data-ttu-id="2b17a-103">列舉代表目前範圍內的所有類型的 TypeDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="2b17a-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b17a-104">語法</span><span class="sxs-lookup"><span data-stu-id="2b17a-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,   
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,   
   [out] ULONG      *pcTypeDefs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2b17a-105">參數</span><span class="sxs-lookup"><span data-stu-id="2b17a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="2b17a-106">[out]新的列舉值指標。</span><span class="sxs-lookup"><span data-stu-id="2b17a-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="2b17a-107">這必須是 NULL 的第一個呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="2b17a-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="2b17a-108">[in]陣列，用來儲存的 TypeDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="2b17a-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="2b17a-109">[in] `rTypeDefs` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="2b17a-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="2b17a-110">[out]傳回的 TypeDef 語彙基元數目`rTypeDefs`。</span><span class="sxs-lookup"><span data-stu-id="2b17a-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b17a-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="2b17a-111">Return Value</span></span>  
  
|<span data-ttu-id="2b17a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2b17a-112">HRESULT</span></span>|<span data-ttu-id="2b17a-113">說明</span><span class="sxs-lookup"><span data-stu-id="2b17a-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="2b17a-114">`EnumTypeDefs`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="2b17a-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="2b17a-115">沒有列舉語彙基元。</span><span class="sxs-lookup"><span data-stu-id="2b17a-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="2b17a-116">在此情況下，`pcTypeDefs`為零。</span><span class="sxs-lookup"><span data-stu-id="2b17a-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b17a-117">備註</span><span class="sxs-lookup"><span data-stu-id="2b17a-117">Remarks</span></span>  
 <span data-ttu-id="2b17a-118">TypeDef 語彙基元所代表的類型，例如類別或介面，以及透過 擴充性機制加入任何型別。</span><span class="sxs-lookup"><span data-stu-id="2b17a-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b17a-119">需求</span><span class="sxs-lookup"><span data-stu-id="2b17a-119">Requirements</span></span>  
 <span data-ttu-id="2b17a-120">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2b17a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b17a-121">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2b17a-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2b17a-122">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2b17a-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2b17a-123">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b17a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b17a-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b17a-124">See Also</span></span>  
 [<span data-ttu-id="2b17a-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="2b17a-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="2b17a-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="2b17a-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
