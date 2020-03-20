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
ms.openlocfilehash: 13220dcfdd260688494d5aebc50f94abf8a82215
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177498"
---
# <a name="imetadataemitsetparamprops-method"></a><span data-ttu-id="6ccef-102">IMetaDataEmit::SetParamProps 方法</span><span class="sxs-lookup"><span data-stu-id="6ccef-102">IMetaDataEmit::SetParamProps Method</span></span>
<span data-ttu-id="6ccef-103">設置或更改由之前調用[IMetaDataEmit：:DefineParam）](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md)定義的方法參數的功能。</span><span class="sxs-lookup"><span data-stu-id="6ccef-103">Sets or changes features of a method parameter that was defined by a prior call to [IMetaDataEmit::DefineParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ccef-104">語法</span><span class="sxs-lookup"><span data-stu-id="6ccef-104">Syntax</span></span>  
  
```cpp  
HRESULT SetParamProps (
    [in]  mdParamDef  pd,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwParamFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ccef-105">參數</span><span class="sxs-lookup"><span data-stu-id="6ccef-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="6ccef-106">[在]目標參數的權杖。</span><span class="sxs-lookup"><span data-stu-id="6ccef-106">[in] The token for the target parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="6ccef-107">[在]Unicode 中參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="6ccef-107">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="6ccef-108">[在]參數的標誌。</span><span class="sxs-lookup"><span data-stu-id="6ccef-108">[in] The flags for the parameter.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="6ccef-109">[在]常量值的ELEMENT_TYPE_\*。</span><span class="sxs-lookup"><span data-stu-id="6ccef-109">[in] The ELEMENT_TYPE_\* for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="6ccef-110">[在]參數的常量值。</span><span class="sxs-lookup"><span data-stu-id="6ccef-110">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="6ccef-111">[在]的大小（Unicode）字元。 `pValue`</span><span class="sxs-lookup"><span data-stu-id="6ccef-111">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ccef-112">需求</span><span class="sxs-lookup"><span data-stu-id="6ccef-112">Requirements</span></span>  
 <span data-ttu-id="6ccef-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6ccef-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ccef-114">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="6ccef-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6ccef-115">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6ccef-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6ccef-116">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ccef-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ccef-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ccef-117">See also</span></span>

- [<span data-ttu-id="6ccef-118">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="6ccef-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="6ccef-119">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="6ccef-119">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
