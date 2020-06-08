---
title: IMetaDataImport::GetParamProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type:
- apiref
ms.openlocfilehash: c2abf2813c6e1a9db4264bded32d9cb9c58a2bcb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491052"
---
# <a name="imetadataimportgetparamprops-method"></a><span data-ttu-id="6e468-102">IMetaDataImport::GetParamProps 方法</span><span class="sxs-lookup"><span data-stu-id="6e468-102">IMetaDataImport::GetParamProps Method</span></span>
<span data-ttu-id="6e468-103">取得指定 ParamDef 語彙基元所參考參數的中繼資料值。</span><span class="sxs-lookup"><span data-stu-id="6e468-103">Gets metadata values for the parameter referenced by the specified ParamDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e468-104">語法</span><span class="sxs-lookup"><span data-stu-id="6e468-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParamProps (  
   [in]  mdParamDef      tk,  
   [out] mdMethodDef     *pmd,  
   [out] ULONG           *pulSequence,  
   [out] LPWSTR          szName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName,  
   [out] DWORD           *pdwAttr,  
   [out] DWORD           *pdwCPlusTypeFlag,  
   [out] UVCP_CONSTANT   *ppValue,  
   [out] ULONG           *pcchValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e468-105">參數</span><span class="sxs-lookup"><span data-stu-id="6e468-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="6e468-106">在ParamDef token，表示要傳回中繼資料的參數。</span><span class="sxs-lookup"><span data-stu-id="6e468-106">[in] A ParamDef token that represents the parameter to return metadata for.</span></span>  
  
 `pmd`  
 <span data-ttu-id="6e468-107">脫銷MethodDef token 的指標，代表接受參數的方法。</span><span class="sxs-lookup"><span data-stu-id="6e468-107">[out] A pointer to a MethodDef token representing the method that takes the parameter.</span></span>  
  
 `pulSequence`  
 <span data-ttu-id="6e468-108">脫銷方法引數清單中參數的序數位置。</span><span class="sxs-lookup"><span data-stu-id="6e468-108">[out] The ordinal position of the parameter in the method argument list.</span></span>  
  
 `szName`  
 <span data-ttu-id="6e468-109">脫銷保存參數名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="6e468-109">[out] A buffer to hold the name of the parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="6e468-110">在所要求的大小（以寬字元為單位） `szName` 。</span><span class="sxs-lookup"><span data-stu-id="6e468-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="6e468-111">脫銷傳回的大小（以寬字元為單位） `szName` 。</span><span class="sxs-lookup"><span data-stu-id="6e468-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="6e468-112">脫銷與參數相關聯之任何屬性旗標的指標。</span><span class="sxs-lookup"><span data-stu-id="6e468-112">[out] A pointer to any attribute flags associated with the parameter.</span></span> <span data-ttu-id="6e468-113">這是值的位元遮罩 `CorParamAttr` 。</span><span class="sxs-lookup"><span data-stu-id="6e468-113">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="6e468-114">脫銷指定參數為之旗標的指標 <xref:System.ValueType> 。</span><span class="sxs-lookup"><span data-stu-id="6e468-114">[out] A pointer to a flag specifying that the parameter is a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="6e468-115">脫銷參數所傳回之常數位串的指標。</span><span class="sxs-lookup"><span data-stu-id="6e468-115">[out] A pointer to a constant string returned by the parameter.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="6e468-116">脫銷的大小 `ppValue` ，以寬字元為單位，如果 `ppValue` 不包含字串，則為零。</span><span class="sxs-lookup"><span data-stu-id="6e468-116">[out] The size of `ppValue` in wide characters, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e468-117">備註</span><span class="sxs-lookup"><span data-stu-id="6e468-117">Remarks</span></span>

<span data-ttu-id="6e468-118">參數的順序值 `pulSequence` 開頭為1。</span><span class="sxs-lookup"><span data-stu-id="6e468-118">The sequence values in `pulSequence` begin with 1 for parameters.</span></span> <span data-ttu-id="6e468-119">傳回值的序號為0。</span><span class="sxs-lookup"><span data-stu-id="6e468-119">A return value has a sequence number of 0.</span></span>

## <a name="requirements"></a><span data-ttu-id="6e468-120">規格需求</span><span class="sxs-lookup"><span data-stu-id="6e468-120">Requirements</span></span>  
 <span data-ttu-id="6e468-121">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6e468-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e468-122">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="6e468-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6e468-123">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6e468-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6e468-124">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e468-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e468-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e468-125">See also</span></span>

- [<span data-ttu-id="6e468-126">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="6e468-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="6e468-127">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="6e468-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
