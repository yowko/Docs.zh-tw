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
ms.openlocfilehash: 5b3f89bb14be0d7128682f8702548545b1e50928
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719524"
---
# <a name="imetadataemitdefineparam-method"></a><span data-ttu-id="fbb7f-102">IMetaDataEmit::DefineParam 方法</span><span class="sxs-lookup"><span data-stu-id="fbb7f-102">IMetaDataEmit::DefineParam Method</span></span>

<span data-ttu-id="fbb7f-103">針對指定之標記所參考的方法，使用指定的簽章建立參數定義，並取得該參數定義的標記。</span><span class="sxs-lookup"><span data-stu-id="fbb7f-103">Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbb7f-104">語法</span><span class="sxs-lookup"><span data-stu-id="fbb7f-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="fbb7f-105">參數</span><span class="sxs-lookup"><span data-stu-id="fbb7f-105">Parameters</span></span>  

 `md`  
 <span data-ttu-id="fbb7f-106">在要定義其參數之方法的標記。</span><span class="sxs-lookup"><span data-stu-id="fbb7f-106">[in] The token for the method whose parameter is being defined.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="fbb7f-107">在參數序號。</span><span class="sxs-lookup"><span data-stu-id="fbb7f-107">[in] The parameter sequence number.</span></span>  
  
 `szName`  
 <span data-ttu-id="fbb7f-108">在Unicode 中參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="fbb7f-108">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="fbb7f-109">在參數的旗標。</span><span class="sxs-lookup"><span data-stu-id="fbb7f-109">[in] Flags for the parameter.</span></span> <span data-ttu-id="fbb7f-110">這是值的位元遮罩 `CorParamAttr` 。</span><span class="sxs-lookup"><span data-stu-id="fbb7f-110">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="fbb7f-111">[in] `ELEMENT_TYPE_` *\** 做為常數值。</span><span class="sxs-lookup"><span data-stu-id="fbb7f-111">[in] `ELEMENT_TYPE_`*\** for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="fbb7f-112">在參數的常數值。</span><span class="sxs-lookup"><span data-stu-id="fbb7f-112">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="fbb7f-113">在的大小（以 Unicode 字元為單位） `pValue` 。</span><span class="sxs-lookup"><span data-stu-id="fbb7f-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
 `ppd`  
 <span data-ttu-id="fbb7f-114">擴展 `mdParamDef` 指派的權杖。</span><span class="sxs-lookup"><span data-stu-id="fbb7f-114">[out] The `mdParamDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbb7f-115">備註</span><span class="sxs-lookup"><span data-stu-id="fbb7f-115">Remarks</span></span>  

 <span data-ttu-id="fbb7f-116">參數開頭為1的順序值 `ulParamSeq` 。</span><span class="sxs-lookup"><span data-stu-id="fbb7f-116">The sequence values in `ulParamSeq` begin with 1 for parameters.</span></span> <span data-ttu-id="fbb7f-117">傳回值的序號為0。</span><span class="sxs-lookup"><span data-stu-id="fbb7f-117">A return value has a sequence number of 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbb7f-118">需求</span><span class="sxs-lookup"><span data-stu-id="fbb7f-118">Requirements</span></span>  

 <span data-ttu-id="fbb7f-119">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fbb7f-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbb7f-120">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="fbb7f-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fbb7f-121">連結 **庫：** 當做 MSCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="fbb7f-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fbb7f-122">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbb7f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbb7f-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbb7f-123">See also</span></span>

- [<span data-ttu-id="fbb7f-124">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="fbb7f-124">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="fbb7f-125">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="fbb7f-125">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
