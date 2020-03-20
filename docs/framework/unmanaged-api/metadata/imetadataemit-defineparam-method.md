---
title: IMetaDataEmit::DefineParam 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type:
- apiref
ms.openlocfilehash: 2807458549db02598ba05f2aa80fa6ea6fbc5a13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177698"
---
# <a name="imetadataemitdefineparam-method"></a><span data-ttu-id="ad886-102">IMetaDataEmit::DefineParam 方法</span><span class="sxs-lookup"><span data-stu-id="ad886-102">IMetaDataEmit::DefineParam Method</span></span>
<span data-ttu-id="ad886-103">為指定權杖引用的方法創建具有指定簽名的參數定義，並獲取該參數定義的權杖。</span><span class="sxs-lookup"><span data-stu-id="ad886-103">Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad886-104">語法</span><span class="sxs-lookup"><span data-stu-id="ad886-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineParam (  
    [in]  mdMethodDef md,
    [in]  ULONG       ulParamSeq,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwParamFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,  
    [in]  ULONG       cchValue,
    [out] mdParamDef  *ppd
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad886-105">參數</span><span class="sxs-lookup"><span data-stu-id="ad886-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="ad886-106">[在]正在定義其參數的方法的權杖。</span><span class="sxs-lookup"><span data-stu-id="ad886-106">[in] The token for the method whose parameter is being defined.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="ad886-107">[在]參數序號。</span><span class="sxs-lookup"><span data-stu-id="ad886-107">[in] The parameter sequence number.</span></span>  
  
 `szName`  
 <span data-ttu-id="ad886-108">[在]Unicode 中參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="ad886-108">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="ad886-109">[在]參數的標誌。</span><span class="sxs-lookup"><span data-stu-id="ad886-109">[in] Flags for the parameter.</span></span> <span data-ttu-id="ad886-110">這是值的`CorParamAttr`位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="ad886-110">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="ad886-111">[在]`ELEMENT_TYPE_` *\**</span><span class="sxs-lookup"><span data-stu-id="ad886-111">[in] `ELEMENT_TYPE_`*\** for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="ad886-112">[在]參數的常量值。</span><span class="sxs-lookup"><span data-stu-id="ad886-112">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="ad886-113">[在]的大小（以 Unicode 字元表示`pValue`）</span><span class="sxs-lookup"><span data-stu-id="ad886-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
 `ppd`  
 <span data-ttu-id="ad886-114">[出]分配的`mdParamDef`權杖。</span><span class="sxs-lookup"><span data-stu-id="ad886-114">[out] The `mdParamDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad886-115">備註</span><span class="sxs-lookup"><span data-stu-id="ad886-115">Remarks</span></span>  
 <span data-ttu-id="ad886-116">中的序列值以`ulParamSeq`1 開頭的參數。</span><span class="sxs-lookup"><span data-stu-id="ad886-116">The sequence values in `ulParamSeq` begin with 1 for parameters.</span></span> <span data-ttu-id="ad886-117">傳回值的序號為 0。</span><span class="sxs-lookup"><span data-stu-id="ad886-117">A return value has a sequence number of 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad886-118">需求</span><span class="sxs-lookup"><span data-stu-id="ad886-118">Requirements</span></span>  
 <span data-ttu-id="ad886-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ad886-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad886-120">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="ad886-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ad886-121">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ad886-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ad886-122">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad886-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad886-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad886-123">See also</span></span>

- [<span data-ttu-id="ad886-124">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="ad886-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ad886-125">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="ad886-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
