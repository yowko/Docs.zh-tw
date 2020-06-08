---
title: IMetaDataEmit2::DefineGenericParam 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineGenericParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineGenericParam
helpviewer_keywords:
- IMetaDataEmit2::DefineGenericParam method [.NET Framework metadata]
- DefineGenericParam method [.NET Framework metadata]
ms.assetid: 47b2a3b6-907d-43dc-858d-1ae7dca1316a
topic_type:
- apiref
ms.openlocfilehash: e4401ea8a70e7ace8d8efc5e0a6d29f6db51b3df
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503805"
---
# <a name="imetadataemit2definegenericparam-method"></a><span data-ttu-id="b082d-102">IMetaDataEmit2::DefineGenericParam 方法</span><span class="sxs-lookup"><span data-stu-id="b082d-102">IMetaDataEmit2::DefineGenericParam Method</span></span>
<span data-ttu-id="b082d-103">建立泛型型別參數的定義，並取得該泛型型別參數的 token。</span><span class="sxs-lookup"><span data-stu-id="b082d-103">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b082d-104">語法</span><span class="sxs-lookup"><span data-stu-id="b082d-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineGenericParam (
    [in]  mdToken         tk,
    [in]  ULONG           ulParamSeq,
    [in]  DWORD           dwParamFlags,
    [in]  LPCWSTR         szname,
    [in]  DWORD           reserved,
    [in]  mdToken         rtkConstraints[],
    [out] mdGenericParam  *pgp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b082d-105">參數</span><span class="sxs-lookup"><span data-stu-id="b082d-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="b082d-106">在`mdTypeDef`或 `mdMethodDef` token，表示要定義泛型參數的方法或構造函式。</span><span class="sxs-lookup"><span data-stu-id="b082d-106">[in] An `mdTypeDef` or `mdMethodDef` token that represents the method or constructor for which to define a generic parameter.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="b082d-107">在泛型參數的索引。</span><span class="sxs-lookup"><span data-stu-id="b082d-107">[in] The index of the generic parameter.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="b082d-108">在[CorGenericParamAttr](corgenericparamattr-enumeration.md)列舉的值，描述泛型參數的類型。</span><span class="sxs-lookup"><span data-stu-id="b082d-108">[in] A value of the [CorGenericParamAttr](corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szname`  
 <span data-ttu-id="b082d-109">在參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="b082d-109">[in] The name of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="b082d-110">在此參數保留供未來擴充性之用。</span><span class="sxs-lookup"><span data-stu-id="b082d-110">[in] This parameter is reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="b082d-111">在類型條件約束之以零結束的陣列。</span><span class="sxs-lookup"><span data-stu-id="b082d-111">[in] A zero-terminated array of type constraints.</span></span> <span data-ttu-id="b082d-112">陣列成員必須是 `mdTypeDef` 、 `mdTypeRef` 或 `mdTypeSpec` 元資料標記。</span><span class="sxs-lookup"><span data-stu-id="b082d-112">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
 `pgp`  
 <span data-ttu-id="b082d-113">脫銷表示泛型參數的 token。</span><span class="sxs-lookup"><span data-stu-id="b082d-113">[out] A token that represents the generic parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b082d-114">規格需求</span><span class="sxs-lookup"><span data-stu-id="b082d-114">Requirements</span></span>  
 <span data-ttu-id="b082d-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b082d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b082d-116">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="b082d-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b082d-117">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="b082d-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b082d-118">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b082d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b082d-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b082d-119">See also</span></span>

- [<span data-ttu-id="b082d-120">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="b082d-120">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="b082d-121">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="b082d-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
