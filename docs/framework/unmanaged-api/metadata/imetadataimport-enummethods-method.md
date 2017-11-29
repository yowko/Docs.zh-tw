---
title: "IMetaDataImport::EnumMethods 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumMethods
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumMethods
helpviewer_keywords:
- IMetaDataImport::EnumMethods method [.NET Framework metadata]
- EnumMethods method [.NET Framework metadata]
ms.assetid: 8cc3b0c3-d97d-4f71-9e7d-ef2a92b4959a
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d56c87d7073886d13e530501168801c6c69d9ce9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenummethods-method"></a><span data-ttu-id="302d2-102">IMetaDataImport::EnumMethods 方法</span><span class="sxs-lookup"><span data-stu-id="302d2-102">IMetaDataImport::EnumMethods Method</span></span>
<span data-ttu-id="302d2-103">列舉代表指定類型方法的 MethodDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="302d2-103">Enumerates MethodDef tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="302d2-104">語法</span><span class="sxs-lookup"><span data-stu-id="302d2-104">Syntax</span></span>  
  
```  
HRESULT EnumMethods (  
   [in, out] HCORENUM   *phEnum,   
   [in]  mdTypeDef      cl,   
   [out] mdMethodDef    rMethods[],   
   [in]  ULONG          cMax,   
   [out] ULONG          *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="302d2-105">參數</span><span class="sxs-lookup"><span data-stu-id="302d2-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="302d2-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="302d2-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="302d2-107">這必須是 NULL 的第一個呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="302d2-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="302d2-108">[in]TypeDef 語彙基元的方法來列舉表示的型別。</span><span class="sxs-lookup"><span data-stu-id="302d2-108">[in] A TypeDef token representing the type with the methods to enumerate.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="302d2-109">[out]要儲存 methoddef 語彙基元的陣列。</span><span class="sxs-lookup"><span data-stu-id="302d2-109">[out] The array to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="302d2-110">[in]大小上限的 MethodDef`rMethods`陣列。</span><span class="sxs-lookup"><span data-stu-id="302d2-110">[in] The maximum size of the MethodDef `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="302d2-111">[out]傳回的 methoddef 語彙基元數目`rMethods`。</span><span class="sxs-lookup"><span data-stu-id="302d2-111">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="302d2-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="302d2-112">Return Value</span></span>  
  
|<span data-ttu-id="302d2-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="302d2-113">HRESULT</span></span>|<span data-ttu-id="302d2-114">說明</span><span class="sxs-lookup"><span data-stu-id="302d2-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="302d2-115">`EnumMethods`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="302d2-115">`EnumMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="302d2-116">沒有列舉 MethodDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="302d2-116">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="302d2-117">在此情況下，`pcTokens`為零。</span><span class="sxs-lookup"><span data-stu-id="302d2-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="302d2-118">需求</span><span class="sxs-lookup"><span data-stu-id="302d2-118">Requirements</span></span>  
 <span data-ttu-id="302d2-119">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="302d2-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="302d2-120">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="302d2-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="302d2-121">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="302d2-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="302d2-122">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="302d2-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="302d2-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="302d2-123">See Also</span></span>  
 [<span data-ttu-id="302d2-124">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="302d2-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="302d2-125">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="302d2-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
