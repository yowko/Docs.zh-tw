---
title: IMetaDataEmit2::SetGenericParamProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SetGenericParamProps
helpviewer_keywords:
- IMetaDataEmit2::SetGenericParamProps method [.NET Framework metadata]
- SetGenericParamProps method [.NET Framework metadata]
ms.assetid: cd93a48d-1fed-4706-bec6-a05dc3b64fbd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4daf24c1712b18d933da702e9e1ef1cbdbfc3639
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62043663"
---
# <a name="imetadataemit2setgenericparamprops-method"></a><span data-ttu-id="3824b-102">IMetaDataEmit2::SetGenericParamProps 方法</span><span class="sxs-lookup"><span data-stu-id="3824b-102">IMetaDataEmit2::SetGenericParamProps Method</span></span>
<span data-ttu-id="3824b-103">設定指定的語彙基元所參考的泛型參數定義的屬性值。</span><span class="sxs-lookup"><span data-stu-id="3824b-103">Sets property values for the generic parameter definition referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3824b-104">語法</span><span class="sxs-lookup"><span data-stu-id="3824b-104">Syntax</span></span>  
  
```  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,   
    [in] DWORD            dwParamFlags,   
    [in] LPCWSTR          szName,   
    [in] DWORD            reserved,   
    [in] mdToken          rtkConstraints[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3824b-105">參數</span><span class="sxs-lookup"><span data-stu-id="3824b-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="3824b-106">[in]如需泛型參數定義為其設定值語彙基元。</span><span class="sxs-lookup"><span data-stu-id="3824b-106">[in] The token for the generic parameter definition for which to set values.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="3824b-107">[in]值為[CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md)描述泛型參數類型的列舉型別。</span><span class="sxs-lookup"><span data-stu-id="3824b-107">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="3824b-108">[in] 選用。</span><span class="sxs-lookup"><span data-stu-id="3824b-108">[in] Optional.</span></span> <span data-ttu-id="3824b-109">要設定值的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="3824b-109">The name of the parameter for which to set values.</span></span>  
  
 `reserved`  
 <span data-ttu-id="3824b-110">[in]保留供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="3824b-110">[in] Reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="3824b-111">[in] 選用。</span><span class="sxs-lookup"><span data-stu-id="3824b-111">[in] Optional.</span></span> <span data-ttu-id="3824b-112">類型條件約束的零結尾的陣列。</span><span class="sxs-lookup"><span data-stu-id="3824b-112">A zero-terminated array of type constraints.</span></span> <span data-ttu-id="3824b-113">陣列成員必須是`mdTypeDef`， `mdTypeRef`，或`mdTypeSpec`中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="3824b-113">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3824b-114">需求</span><span class="sxs-lookup"><span data-stu-id="3824b-114">Requirements</span></span>  
 <span data-ttu-id="3824b-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3824b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3824b-116">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3824b-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3824b-117">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3824b-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3824b-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3824b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3824b-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3824b-119">See also</span></span>

- [<span data-ttu-id="3824b-120">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="3824b-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="3824b-121">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="3824b-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
