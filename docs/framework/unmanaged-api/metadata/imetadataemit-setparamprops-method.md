---
title: "IMetaDataEmit::SetParamProps 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetParamProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetParamProps
helpviewer_keywords:
- IMetaDataEmit::SetParamProps method [.NET Framework metadata]
- SetParamProps method [.NET Framework metadata]
ms.assetid: a95a3908-9f87-4084-937e-8e01ef03ad63
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e8ada9deddf8528321797c1f9bd06b5b775ac4bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsetparamprops-method"></a><span data-ttu-id="fc8e9-102">IMetaDataEmit::SetParamProps 方法</span><span class="sxs-lookup"><span data-stu-id="fc8e9-102">IMetaDataEmit::SetParamProps Method</span></span>
<span data-ttu-id="fc8e9-103">設定或變更在先前呼叫所定義的方法參數的功能[imetadataemit:: Defineparam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md)。</span><span class="sxs-lookup"><span data-stu-id="fc8e9-103">Sets or changes features of a method parameter that was defined by a prior call to [IMetaDataEmit::DefineParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc8e9-104">語法</span><span class="sxs-lookup"><span data-stu-id="fc8e9-104">Syntax</span></span>  
  
```  
HRESULT SetParamProps (   
    [in]  mdParamDef  pd,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwParamFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fc8e9-105">參數</span><span class="sxs-lookup"><span data-stu-id="fc8e9-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="fc8e9-106">[in]目標參數的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="fc8e9-106">[in] The token for the target parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="fc8e9-107">[in]以 Unicode 參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="fc8e9-107">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="fc8e9-108">[in]參數的旗標。</span><span class="sxs-lookup"><span data-stu-id="fc8e9-108">[in] The flags for the parameter.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="fc8e9-109">[in]ELEMENT_TYPE_ * 常數的值。</span><span class="sxs-lookup"><span data-stu-id="fc8e9-109">[in] The ELEMENT_TYPE_* for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="fc8e9-110">[in]參數的常值。</span><span class="sxs-lookup"><span data-stu-id="fc8e9-110">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="fc8e9-111">[in]以 (Unicode) 字元為單位的大小`pValue`。</span><span class="sxs-lookup"><span data-stu-id="fc8e9-111">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc8e9-112">需求</span><span class="sxs-lookup"><span data-stu-id="fc8e9-112">Requirements</span></span>  
 <span data-ttu-id="fc8e9-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fc8e9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc8e9-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fc8e9-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fc8e9-115">**程式庫：**做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="fc8e9-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fc8e9-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc8e9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc8e9-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="fc8e9-117">See Also</span></span>  
 [<span data-ttu-id="fc8e9-118">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="fc8e9-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="fc8e9-119">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="fc8e9-119">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
