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
ms.openlocfilehash: 8858e692d66f7b34a66334bd4e8b906dd12962ba
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701987"
---
# <a name="imetadataemit2setgenericparamprops-method"></a><span data-ttu-id="70c8a-102">IMetaDataEmit2::SetGenericParamProps 方法</span><span class="sxs-lookup"><span data-stu-id="70c8a-102">IMetaDataEmit2::SetGenericParamProps Method</span></span>

<span data-ttu-id="70c8a-103">設定指定之標記所參考之泛型參數定義的屬性值。</span><span class="sxs-lookup"><span data-stu-id="70c8a-103">Sets property values for the generic parameter definition referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70c8a-104">語法</span><span class="sxs-lookup"><span data-stu-id="70c8a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,
    [in] DWORD            dwParamFlags,
    [in] LPCWSTR          szName,
    [in] DWORD            reserved,
    [in] mdToken          rtkConstraints[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70c8a-105">參數</span><span class="sxs-lookup"><span data-stu-id="70c8a-105">Parameters</span></span>  

 `gp`  
 <span data-ttu-id="70c8a-106">在要設定其值之泛型參數定義的標記。</span><span class="sxs-lookup"><span data-stu-id="70c8a-106">[in] The token for the generic parameter definition for which to set values.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="70c8a-107">在描述泛型參數之類型的 [CorGenericParamAttr](corgenericparamattr-enumeration.md) 列舉值。</span><span class="sxs-lookup"><span data-stu-id="70c8a-107">[in] A value of the [CorGenericParamAttr](corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="70c8a-108">[in] 選用。</span><span class="sxs-lookup"><span data-stu-id="70c8a-108">[in] Optional.</span></span> <span data-ttu-id="70c8a-109">要設定其值的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="70c8a-109">The name of the parameter for which to set values.</span></span>  
  
 `reserved`  
 <span data-ttu-id="70c8a-110">在保留供未來擴充性之用。</span><span class="sxs-lookup"><span data-stu-id="70c8a-110">[in] Reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="70c8a-111">[in] 選用。</span><span class="sxs-lookup"><span data-stu-id="70c8a-111">[in] Optional.</span></span> <span data-ttu-id="70c8a-112">以零結束的型別條件約束陣列。</span><span class="sxs-lookup"><span data-stu-id="70c8a-112">A zero-terminated array of type constraints.</span></span> <span data-ttu-id="70c8a-113">陣列成員必須是 `mdTypeDef` 、 `mdTypeRef` 或 `mdTypeSpec` 元資料標記。</span><span class="sxs-lookup"><span data-stu-id="70c8a-113">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70c8a-114">需求</span><span class="sxs-lookup"><span data-stu-id="70c8a-114">Requirements</span></span>  

 <span data-ttu-id="70c8a-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="70c8a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70c8a-116">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="70c8a-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="70c8a-117">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="70c8a-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="70c8a-118">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70c8a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70c8a-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70c8a-119">See also</span></span>

- [<span data-ttu-id="70c8a-120">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="70c8a-120">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="70c8a-121">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="70c8a-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
