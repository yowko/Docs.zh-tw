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
ms.openlocfilehash: 5c81bc82e19bce658336e4860a61f2721e17423d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431696"
---
# <a name="imetadataemitdefineparam-method"></a><span data-ttu-id="266db-102">IMetaDataEmit::DefineParam 方法</span><span class="sxs-lookup"><span data-stu-id="266db-102">IMetaDataEmit::DefineParam Method</span></span>
<span data-ttu-id="266db-103">針對指定之標記所參考的方法，使用指定的簽章建立參數定義，並取得該參數定義的 token。</span><span class="sxs-lookup"><span data-stu-id="266db-103">Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="266db-104">語法</span><span class="sxs-lookup"><span data-stu-id="266db-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="266db-105">參數</span><span class="sxs-lookup"><span data-stu-id="266db-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="266db-106">在要定義其參數之方法的 token。</span><span class="sxs-lookup"><span data-stu-id="266db-106">[in] The token for the method whose parameter is being defined.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="266db-107">在參數序號。</span><span class="sxs-lookup"><span data-stu-id="266db-107">[in] The parameter sequence number.</span></span>  
  
 `szName`  
 <span data-ttu-id="266db-108">在Unicode 中的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="266db-108">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="266db-109">在參數的旗標。</span><span class="sxs-lookup"><span data-stu-id="266db-109">[in] Flags for the parameter.</span></span> <span data-ttu-id="266db-110">這是 `CorParamAttr` 值的位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="266db-110">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="266db-111">[in] `ELEMENT_TYPE_`常數值的 *\** 。</span><span class="sxs-lookup"><span data-stu-id="266db-111">[in] `ELEMENT_TYPE_`*\** for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="266db-112">在參數的常數值。</span><span class="sxs-lookup"><span data-stu-id="266db-112">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="266db-113">在`pValue`的大小，以 Unicode 字元為單位。</span><span class="sxs-lookup"><span data-stu-id="266db-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
 `ppd`  
 <span data-ttu-id="266db-114">脫銷指派的 `mdParamDef` token。</span><span class="sxs-lookup"><span data-stu-id="266db-114">[out] The `mdParamDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="266db-115">備註</span><span class="sxs-lookup"><span data-stu-id="266db-115">Remarks</span></span>  
 <span data-ttu-id="266db-116">`ulParamSeq` 中的順序值會以1為參數開頭。</span><span class="sxs-lookup"><span data-stu-id="266db-116">The sequence values in `ulParamSeq` begin with 1 for parameters.</span></span> <span data-ttu-id="266db-117">傳回值的序號為0。</span><span class="sxs-lookup"><span data-stu-id="266db-117">A return value has a sequence number of 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="266db-118">需求</span><span class="sxs-lookup"><span data-stu-id="266db-118">Requirements</span></span>  
 <span data-ttu-id="266db-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="266db-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="266db-120">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="266db-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="266db-121">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="266db-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="266db-122">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="266db-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="266db-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="266db-123">See also</span></span>

- [<span data-ttu-id="266db-124">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="266db-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="266db-125">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="266db-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
