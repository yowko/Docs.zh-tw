---
title: IMetaDataEmit::SetParamProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParamProps
helpviewer_keywords:
- IMetaDataEmit::SetParamProps method [.NET Framework metadata]
- SetParamProps method [.NET Framework metadata]
ms.assetid: a95a3908-9f87-4084-937e-8e01ef03ad63
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b2885d89883ab6312c2ad9d3feac405eef2fbede
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693687"
---
# <a name="imetadataemitsetparamprops-method"></a><span data-ttu-id="00a46-102">IMetaDataEmit::SetParamProps 方法</span><span class="sxs-lookup"><span data-stu-id="00a46-102">IMetaDataEmit::SetParamProps Method</span></span>
<span data-ttu-id="00a46-103">設定或變更已由先前呼叫的方法參數的功能[imetadataemit:: Defineparam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md)。</span><span class="sxs-lookup"><span data-stu-id="00a46-103">Sets or changes features of a method parameter that was defined by a prior call to [IMetaDataEmit::DefineParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00a46-104">語法</span><span class="sxs-lookup"><span data-stu-id="00a46-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="00a46-105">參數</span><span class="sxs-lookup"><span data-stu-id="00a46-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="00a46-106">[in]目標參數的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="00a46-106">[in] The token for the target parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="00a46-107">[in]以 Unicode 參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="00a46-107">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="00a46-108">[in]參數的旗標。</span><span class="sxs-lookup"><span data-stu-id="00a46-108">[in] The flags for the parameter.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="00a46-109">[in]ELEMENT_TYPE_ \* 常數的值。</span><span class="sxs-lookup"><span data-stu-id="00a46-109">[in] The ELEMENT_TYPE_\* for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="00a46-110">[in]參數的常值。</span><span class="sxs-lookup"><span data-stu-id="00a46-110">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="00a46-111">[in](Unicode) 字元的大小`pValue`。</span><span class="sxs-lookup"><span data-stu-id="00a46-111">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00a46-112">需求</span><span class="sxs-lookup"><span data-stu-id="00a46-112">Requirements</span></span>  
 <span data-ttu-id="00a46-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="00a46-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00a46-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="00a46-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="00a46-115">**程式庫：** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="00a46-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="00a46-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00a46-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00a46-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00a46-117">See also</span></span>
- [<span data-ttu-id="00a46-118">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="00a46-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="00a46-119">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="00a46-119">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
