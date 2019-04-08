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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 86711d107636505ab7aa23f0f72f70bd3e27635d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59167768"
---
# <a name="imetadataemitdefineparam-method"></a><span data-ttu-id="54fa0-102">IMetaDataEmit::DefineParam 方法</span><span class="sxs-lookup"><span data-stu-id="54fa0-102">IMetaDataEmit::DefineParam Method</span></span>
<span data-ttu-id="54fa0-103">使用指定的語彙基元所參考的方法指定的簽章建立的參數定義，並取得該參數定義的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="54fa0-103">Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54fa0-104">語法</span><span class="sxs-lookup"><span data-stu-id="54fa0-104">Syntax</span></span>  
  
```  
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
  
## <a name="parameters"></a><span data-ttu-id="54fa0-105">參數</span><span class="sxs-lookup"><span data-stu-id="54fa0-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="54fa0-106">[in]正在定義其參數的方法之語彙基元。</span><span class="sxs-lookup"><span data-stu-id="54fa0-106">[in] The token for the method whose parameter is being defined.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="54fa0-107">[in]參數的順序編號。</span><span class="sxs-lookup"><span data-stu-id="54fa0-107">[in] The parameter sequence number.</span></span>  
  
 `szName`  
 <span data-ttu-id="54fa0-108">[in]以 Unicode 參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="54fa0-108">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="54fa0-109">[in]參數的旗標。</span><span class="sxs-lookup"><span data-stu-id="54fa0-109">[in] Flags for the parameter.</span></span> <span data-ttu-id="54fa0-110">這是位元遮罩`CorParamAttr`值。</span><span class="sxs-lookup"><span data-stu-id="54fa0-110">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="54fa0-111">[in]`ELEMENT_TYPE_` *\** 常數的值。</span><span class="sxs-lookup"><span data-stu-id="54fa0-111">[in] `ELEMENT_TYPE_`*\** for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="54fa0-112">[in]參數的常值。</span><span class="sxs-lookup"><span data-stu-id="54fa0-112">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="54fa0-113">[in]大小，以 Unicode 字元的`pValue`。</span><span class="sxs-lookup"><span data-stu-id="54fa0-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
 `ppd`  
 <span data-ttu-id="54fa0-114">[out]`mdParamDef`指派權杖。</span><span class="sxs-lookup"><span data-stu-id="54fa0-114">[out] The `mdParamDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54fa0-115">備註</span><span class="sxs-lookup"><span data-stu-id="54fa0-115">Remarks</span></span>  
 <span data-ttu-id="54fa0-116">中的值序列`ulParamSeq`參數 1 為開頭。</span><span class="sxs-lookup"><span data-stu-id="54fa0-116">The sequence values in `ulParamSeq` begin with 1 for parameters.</span></span> <span data-ttu-id="54fa0-117">傳回值具有 0 的序號。</span><span class="sxs-lookup"><span data-stu-id="54fa0-117">A return value has a sequence number of 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54fa0-118">需求</span><span class="sxs-lookup"><span data-stu-id="54fa0-118">Requirements</span></span>  
 <span data-ttu-id="54fa0-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="54fa0-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54fa0-120">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="54fa0-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="54fa0-121">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="54fa0-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="54fa0-122">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="54fa0-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="54fa0-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54fa0-123">See also</span></span>

- [<span data-ttu-id="54fa0-124">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="54fa0-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="54fa0-125">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="54fa0-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
