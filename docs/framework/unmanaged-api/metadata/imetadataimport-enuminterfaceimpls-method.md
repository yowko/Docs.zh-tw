---
title: "IMetaDataImport::EnumInterfaceImpls 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumInterfaceImpls
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 646d65ff81795ce0558651db9c3fe1bc7205ae08
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="acab3-102">IMetaDataImport::EnumInterfaceImpls 方法</span><span class="sxs-lookup"><span data-stu-id="acab3-102">IMetaDataImport::EnumInterfaceImpls Method</span></span>
<span data-ttu-id="acab3-103">列舉代表介面實作的 MethodDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="acab3-103">Enumerates MethodDef tokens representing interface implementations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acab3-104">語法</span><span class="sxs-lookup"><span data-stu-id="acab3-104">Syntax</span></span>  
  
```  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,   
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],   
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="acab3-105">參數</span><span class="sxs-lookup"><span data-stu-id="acab3-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="acab3-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="acab3-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="acab3-107">[in]代表介面實作的 methoddef 語彙基元是要列舉的 TypeDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="acab3-107">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="acab3-108">[out]陣列，用來儲存 methoddef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="acab3-108">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="acab3-109">[in] `rImpls` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="acab3-109">[in] The maximum size of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="acab3-110">[out]權杖中傳回的實際數目`rImpls`。</span><span class="sxs-lookup"><span data-stu-id="acab3-110">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="acab3-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="acab3-111">Return Value</span></span>  
  
|<span data-ttu-id="acab3-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="acab3-112">HRESULT</span></span>|<span data-ttu-id="acab3-113">描述</span><span class="sxs-lookup"><span data-stu-id="acab3-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="acab3-114">`EnumInterfaceImpls`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="acab3-114">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="acab3-115">沒有列舉 MethodDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="acab3-115">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="acab3-116">在此情況下，`pcImpls`設為零。</span><span class="sxs-lookup"><span data-stu-id="acab3-116">In that case, `pcImpls` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="acab3-117">需求</span><span class="sxs-lookup"><span data-stu-id="acab3-117">Requirements</span></span>  
 <span data-ttu-id="acab3-118">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="acab3-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acab3-119">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="acab3-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="acab3-120">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="acab3-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="acab3-121">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acab3-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acab3-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="acab3-122">See Also</span></span>  
 [<span data-ttu-id="acab3-123">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="acab3-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="acab3-124">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="acab3-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
