---
title: IMetaDataEmit::SetFieldProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldProps
helpviewer_keywords:
- IMetaDataEmit::SetFieldProps method [.NET Framework metadata]
- SetFieldProps method [.NET Framework metadata]
ms.assetid: 47132dda-fa92-4bd1-ae4b-24cd9a60665a
topic_type:
- apiref
ms.openlocfilehash: b921118f7c43edef3c07cbb34cbbd9119d36ce51
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177557"
---
# <a name="imetadataemitsetfieldprops-method"></a><span data-ttu-id="367e5-102">IMetaDataEmit::SetFieldProps 方法</span><span class="sxs-lookup"><span data-stu-id="367e5-102">IMetaDataEmit::SetFieldProps Method</span></span>
<span data-ttu-id="367e5-103">設置或更新指定欄位權杖引用的欄位的預設值。</span><span class="sxs-lookup"><span data-stu-id="367e5-103">Sets or updates the default value for the field referenced by the specified field token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="367e5-104">語法</span><span class="sxs-lookup"><span data-stu-id="367e5-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,
    [in]  DWORD       dwFieldFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="367e5-105">參數</span><span class="sxs-lookup"><span data-stu-id="367e5-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="367e5-106">[在]目標欄位的權杖。</span><span class="sxs-lookup"><span data-stu-id="367e5-106">[in] The token for the target field.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="367e5-107">[在]欄位屬性。</span><span class="sxs-lookup"><span data-stu-id="367e5-107">[in] Field attributes.</span></span> <span data-ttu-id="367e5-108">這是值的`CorFieldAttr`位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="367e5-108">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="367e5-109">[在]常`ELEMENT_TYPE_`*\** 量值的 。</span><span class="sxs-lookup"><span data-stu-id="367e5-109">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="367e5-110">這是一個`CorElementType`值。</span><span class="sxs-lookup"><span data-stu-id="367e5-110">This is a `CorElementType` value.</span></span> <span data-ttu-id="367e5-111">如果未定義常量，則將此值設置為`ELEMENT_TYPE_END`。</span><span class="sxs-lookup"><span data-stu-id="367e5-111">If a constant is not being defined, set this value to `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="367e5-112">[在]欄位的常量值。</span><span class="sxs-lookup"><span data-stu-id="367e5-112">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="367e5-113">[在]的大小（以 Unicode 字元表示`pValue`）</span><span class="sxs-lookup"><span data-stu-id="367e5-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="367e5-114">需求</span><span class="sxs-lookup"><span data-stu-id="367e5-114">Requirements</span></span>  
 <span data-ttu-id="367e5-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="367e5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="367e5-116">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="367e5-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="367e5-117">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="367e5-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="367e5-118">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="367e5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="367e5-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="367e5-119">See also</span></span>

- [<span data-ttu-id="367e5-120">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="367e5-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="367e5-121">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="367e5-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
