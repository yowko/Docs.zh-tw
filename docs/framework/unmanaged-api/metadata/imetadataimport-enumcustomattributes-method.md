---
title: "IMetaDataImport::EnumCustomAttributes 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumCustomAttributes
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method [.NET Framework metadata]
- IMetaDataImport::EnumCustomAttributes method [.NET Framework metadata]
ms.assetid: 798513a0-68b1-4d04-bc5b-782a4445ea68
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 78a642ab3c9766ba32537e24814b3b0536df67c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumcustomattributes-method"></a><span data-ttu-id="9c03c-102">IMetaDataImport::EnumCustomAttributes 方法</span><span class="sxs-lookup"><span data-stu-id="9c03c-102">IMetaDataImport::EnumCustomAttributes Method</span></span>
<span data-ttu-id="9c03c-103">列舉與指定的型別或成員相關聯的自訂屬性定義語彙基元。</span><span class="sxs-lookup"><span data-stu-id="9c03c-103">Enumerates custom attribute-definition tokens associated with the specified type or member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c03c-104">語法</span><span class="sxs-lookup"><span data-stu-id="9c03c-104">Syntax</span></span>  
  
```  
HRESULT EnumCustomAttributes (   
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,   
   [in]  mdToken            tkType,   
   [out] mdCustomAttribute  rCustomAttributes[],   
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9c03c-105">參數</span><span class="sxs-lookup"><span data-stu-id="9c03c-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="9c03c-106">[in、 out]傳回列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="9c03c-106">[in, out] A pointer to the returned enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="9c03c-107">[in]語彙基元範圍的列舉型別，則為零的所有自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="9c03c-107">[in] A token for the scope of the enumeration, or zero for all custom attributes.</span></span>  
  
 `tkType`  
 <span data-ttu-id="9c03c-108">[in]要列舉的屬性類型的建構函式的語彙基元或`null`所有類型。</span><span class="sxs-lookup"><span data-stu-id="9c03c-108">[in] A token for the constructor of the type of the attributes to be enumerated, or `null` for all types.</span></span>  
  
 `rCustomAttributes`  
 <span data-ttu-id="9c03c-109">[out]自訂屬性的語彙基元的陣列。</span><span class="sxs-lookup"><span data-stu-id="9c03c-109">[out] An array of custom attribute tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="9c03c-110">[in] `rCustomAttributes` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="9c03c-110">[in] The maximum size of the `rCustomAttributes` array.</span></span>  
  
 `pcCustomAttributes`  
 <span data-ttu-id="9c03c-111">[out，optional]語彙基元值中傳回的實際數目`rCustomAttributes`。</span><span class="sxs-lookup"><span data-stu-id="9c03c-111">[out, optional] The actual number of token values returned in `rCustomAttributes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9c03c-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="9c03c-112">Return Value</span></span>  
  
|<span data-ttu-id="9c03c-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9c03c-113">HRESULT</span></span>|<span data-ttu-id="9c03c-114">說明</span><span class="sxs-lookup"><span data-stu-id="9c03c-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="9c03c-115">`EnumCustomAttributes`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="9c03c-115">`EnumCustomAttributes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="9c03c-116">沒有自訂屬性列舉。</span><span class="sxs-lookup"><span data-stu-id="9c03c-116">There are no custom attributes to enumerate.</span></span> <span data-ttu-id="9c03c-117">在此情況下，`pcCustomAttributes`為零。</span><span class="sxs-lookup"><span data-stu-id="9c03c-117">In that case, `pcCustomAttributes` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9c03c-118">需求</span><span class="sxs-lookup"><span data-stu-id="9c03c-118">Requirements</span></span>  
 <span data-ttu-id="9c03c-119">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9c03c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c03c-120">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9c03c-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9c03c-121">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9c03c-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9c03c-122">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c03c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c03c-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c03c-123">See Also</span></span>  
 [<span data-ttu-id="9c03c-124">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="9c03c-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="9c03c-125">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="9c03c-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
