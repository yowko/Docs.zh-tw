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
ms.openlocfilehash: c9ff918121e7bb4ee972e674207810358b3f36f2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712907"
---
# <a name="imetadataemit2definegenericparam-method"></a><span data-ttu-id="d440d-102">IMetaDataEmit2::DefineGenericParam 方法</span><span class="sxs-lookup"><span data-stu-id="d440d-102">IMetaDataEmit2::DefineGenericParam Method</span></span>

<span data-ttu-id="d440d-103">建立泛型型別參數的定義，並取得該泛型型別參數的標記。</span><span class="sxs-lookup"><span data-stu-id="d440d-103">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d440d-104">語法</span><span class="sxs-lookup"><span data-stu-id="d440d-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d440d-105">參數</span><span class="sxs-lookup"><span data-stu-id="d440d-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="d440d-106">在 `mdTypeDef` 或 `mdMethodDef` token，表示要定義泛型參數的方法或函式。</span><span class="sxs-lookup"><span data-stu-id="d440d-106">[in] An `mdTypeDef` or `mdMethodDef` token that represents the method or constructor for which to define a generic parameter.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="d440d-107">在泛型參數的索引。</span><span class="sxs-lookup"><span data-stu-id="d440d-107">[in] The index of the generic parameter.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="d440d-108">在描述泛型參數之類型的 [CorGenericParamAttr](corgenericparamattr-enumeration.md) 列舉值。</span><span class="sxs-lookup"><span data-stu-id="d440d-108">[in] A value of the [CorGenericParamAttr](corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szname`  
 <span data-ttu-id="d440d-109">在參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="d440d-109">[in] The name of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="d440d-110">在此參數保留給未來的擴充性。</span><span class="sxs-lookup"><span data-stu-id="d440d-110">[in] This parameter is reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="d440d-111">在以零結束的型別條件約束陣列。</span><span class="sxs-lookup"><span data-stu-id="d440d-111">[in] A zero-terminated array of type constraints.</span></span> <span data-ttu-id="d440d-112">陣列成員必須是 `mdTypeDef` 、 `mdTypeRef` 或 `mdTypeSpec` 元資料標記。</span><span class="sxs-lookup"><span data-stu-id="d440d-112">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
 `pgp`  
 <span data-ttu-id="d440d-113">擴展表示泛型參數的 token。</span><span class="sxs-lookup"><span data-stu-id="d440d-113">[out] A token that represents the generic parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d440d-114">需求</span><span class="sxs-lookup"><span data-stu-id="d440d-114">Requirements</span></span>  

 <span data-ttu-id="d440d-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d440d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d440d-116">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="d440d-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d440d-117">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="d440d-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d440d-118">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d440d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d440d-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d440d-119">See also</span></span>

- [<span data-ttu-id="d440d-120">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="d440d-120">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="d440d-121">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="d440d-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
