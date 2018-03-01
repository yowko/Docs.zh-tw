---
title: "IMetaDataImport::EnumMethods 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport.EnumMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethods
helpviewer_keywords:
- IMetaDataImport::EnumMethods method [.NET Framework metadata]
- EnumMethods method [.NET Framework metadata]
ms.assetid: 8cc3b0c3-d97d-4f71-9e7d-ef2a92b4959a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4052bcd07ec5abd3c560569b59600123350e810c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenummethods-method"></a><span data-ttu-id="7ebd9-102">IMetaDataImport::EnumMethods 方法</span><span class="sxs-lookup"><span data-stu-id="7ebd9-102">IMetaDataImport::EnumMethods Method</span></span>
<span data-ttu-id="7ebd9-103">列舉代表指定類型方法的 MethodDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="7ebd9-103">Enumerates MethodDef tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ebd9-104">語法</span><span class="sxs-lookup"><span data-stu-id="7ebd9-104">Syntax</span></span>  
  
```  
HRESULT EnumMethods (  
   [in, out] HCORENUM   *phEnum,   
   [in]  mdTypeDef      cl,   
   [out] mdMethodDef    rMethods[],   
   [in]  ULONG          cMax,   
   [out] ULONG          *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7ebd9-105">參數</span><span class="sxs-lookup"><span data-stu-id="7ebd9-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="7ebd9-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="7ebd9-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="7ebd9-107">這必須是 NULL 的第一個呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="7ebd9-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="7ebd9-108">[in]TypeDef 語彙基元的方法來列舉表示的型別。</span><span class="sxs-lookup"><span data-stu-id="7ebd9-108">[in] A TypeDef token representing the type with the methods to enumerate.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="7ebd9-109">[out]要儲存 methoddef 語彙基元的陣列。</span><span class="sxs-lookup"><span data-stu-id="7ebd9-109">[out] The array to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="7ebd9-110">[in]大小上限的 MethodDef`rMethods`陣列。</span><span class="sxs-lookup"><span data-stu-id="7ebd9-110">[in] The maximum size of the MethodDef `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="7ebd9-111">[out]傳回的 methoddef 語彙基元數目`rMethods`。</span><span class="sxs-lookup"><span data-stu-id="7ebd9-111">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7ebd9-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="7ebd9-112">Return Value</span></span>  
  
|<span data-ttu-id="7ebd9-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7ebd9-113">HRESULT</span></span>|<span data-ttu-id="7ebd9-114">描述</span><span class="sxs-lookup"><span data-stu-id="7ebd9-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="7ebd9-115">`EnumMethods`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="7ebd9-115">`EnumMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="7ebd9-116">沒有列舉 MethodDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="7ebd9-116">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="7ebd9-117">在此情況下，`pcTokens`為零。</span><span class="sxs-lookup"><span data-stu-id="7ebd9-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7ebd9-118">需求</span><span class="sxs-lookup"><span data-stu-id="7ebd9-118">Requirements</span></span>  
 <span data-ttu-id="7ebd9-119">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7ebd9-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ebd9-120">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7ebd9-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7ebd9-121">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7ebd9-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7ebd9-122">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ebd9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ebd9-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="7ebd9-123">See Also</span></span>  
 [<span data-ttu-id="7ebd9-124">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="7ebd9-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="7ebd9-125">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="7ebd9-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
