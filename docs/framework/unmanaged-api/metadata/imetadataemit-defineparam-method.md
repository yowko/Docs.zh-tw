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
ms.openlocfilehash: 5d49ac70aceb76f69711ea4bf514f69697ac156c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447368"
---
# <a name="imetadataemitdefineparam-method"></a><span data-ttu-id="00f30-102">IMetaDataEmit::DefineParam 方法</span><span class="sxs-lookup"><span data-stu-id="00f30-102">IMetaDataEmit::DefineParam Method</span></span>
<span data-ttu-id="00f30-103">建立與指定的簽章與指定的語彙基元所參考的方法參數的定義，並取得該參數定義的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="00f30-103">Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00f30-104">語法</span><span class="sxs-lookup"><span data-stu-id="00f30-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="00f30-105">參數</span><span class="sxs-lookup"><span data-stu-id="00f30-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="00f30-106">[in]正在定義其參數的方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="00f30-106">[in] The token for the method whose parameter is being defined.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="00f30-107">[in]參數的順序編號。</span><span class="sxs-lookup"><span data-stu-id="00f30-107">[in] The parameter sequence number.</span></span>  
  
 `szName`  
 <span data-ttu-id="00f30-108">[in]以 Unicode 參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="00f30-108">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="00f30-109">[in]參數的旗標。</span><span class="sxs-lookup"><span data-stu-id="00f30-109">[in] Flags for the parameter.</span></span> <span data-ttu-id="00f30-110">這是位元遮罩`CorParamAttr`值。</span><span class="sxs-lookup"><span data-stu-id="00f30-110">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="00f30-111">[in]`ELEMENT_TYPE_` *\** 常數的值。</span><span class="sxs-lookup"><span data-stu-id="00f30-111">[in] `ELEMENT_TYPE_`*\** for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="00f30-112">[in]參數的常值。</span><span class="sxs-lookup"><span data-stu-id="00f30-112">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="00f30-113">[in]大小，以 Unicode 字元的`pValue`。</span><span class="sxs-lookup"><span data-stu-id="00f30-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
 `ppd`  
 <span data-ttu-id="00f30-114">[out]`mdParamDef`指派的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="00f30-114">[out] The `mdParamDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00f30-115">備註</span><span class="sxs-lookup"><span data-stu-id="00f30-115">Remarks</span></span>  
 <span data-ttu-id="00f30-116">中的值序列`ulParamSeq`參數 1 為開頭。</span><span class="sxs-lookup"><span data-stu-id="00f30-116">The sequence values in `ulParamSeq` begin with 1 for parameters.</span></span> <span data-ttu-id="00f30-117">傳回值具有 0 的序號。</span><span class="sxs-lookup"><span data-stu-id="00f30-117">A return value has a sequence number of 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00f30-118">需求</span><span class="sxs-lookup"><span data-stu-id="00f30-118">Requirements</span></span>  
 <span data-ttu-id="00f30-119">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="00f30-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00f30-120">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="00f30-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="00f30-121">**程式庫：** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="00f30-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="00f30-122">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00f30-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00f30-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00f30-123">See Also</span></span>  
 [<span data-ttu-id="00f30-124">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="00f30-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="00f30-125">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="00f30-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
