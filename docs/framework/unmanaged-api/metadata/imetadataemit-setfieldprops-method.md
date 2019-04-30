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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 94ba607669b4b1ca68294470cf1cc4fb27464d28
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992481"
---
# <a name="imetadataemitsetfieldprops-method"></a><span data-ttu-id="ceabd-102">IMetaDataEmit::SetFieldProps 方法</span><span class="sxs-lookup"><span data-stu-id="ceabd-102">IMetaDataEmit::SetFieldProps Method</span></span>
<span data-ttu-id="ceabd-103">設定或更新指定的欄位之語彙基元所參考之欄位的預設值。</span><span class="sxs-lookup"><span data-stu-id="ceabd-103">Sets or updates the default value for the field referenced by the specified field token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ceabd-104">語法</span><span class="sxs-lookup"><span data-stu-id="ceabd-104">Syntax</span></span>  
  
```  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,   
    [in]  DWORD       dwFieldFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ceabd-105">參數</span><span class="sxs-lookup"><span data-stu-id="ceabd-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="ceabd-106">[in]目標欄位的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="ceabd-106">[in] The token for the target field.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="ceabd-107">[in]欄位屬性。</span><span class="sxs-lookup"><span data-stu-id="ceabd-107">[in] Field attributes.</span></span> <span data-ttu-id="ceabd-108">這是位元遮罩`CorFieldAttr`值。</span><span class="sxs-lookup"><span data-stu-id="ceabd-108">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="ceabd-109">[in]`ELEMENT_TYPE_` *\** 常數的值。</span><span class="sxs-lookup"><span data-stu-id="ceabd-109">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="ceabd-110">這是`CorElementType`值。</span><span class="sxs-lookup"><span data-stu-id="ceabd-110">This is a `CorElementType` value.</span></span> <span data-ttu-id="ceabd-111">如果未定義常數，將此值設定為`ELEMENT_TYPE_END`。</span><span class="sxs-lookup"><span data-stu-id="ceabd-111">If a constant is not being defined, set this value to `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="ceabd-112">[in]欄位的常值。</span><span class="sxs-lookup"><span data-stu-id="ceabd-112">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="ceabd-113">[in]大小，以 Unicode 字元的`pValue`。</span><span class="sxs-lookup"><span data-stu-id="ceabd-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ceabd-114">需求</span><span class="sxs-lookup"><span data-stu-id="ceabd-114">Requirements</span></span>  
 <span data-ttu-id="ceabd-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ceabd-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ceabd-116">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ceabd-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ceabd-117">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ceabd-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ceabd-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ceabd-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceabd-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ceabd-119">See also</span></span>

- [<span data-ttu-id="ceabd-120">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="ceabd-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ceabd-121">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="ceabd-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
