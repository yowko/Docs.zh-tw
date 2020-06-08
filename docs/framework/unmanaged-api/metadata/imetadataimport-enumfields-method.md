---
title: IMetaDataImport::EnumFields 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFields
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFields
helpviewer_keywords:
- EnumFields method [.NET Framework metadata]
- IMetaDataImport::EnumFields method [.NET Framework metadata]
ms.assetid: 1d23247e-c58c-45db-afd8-83aa89cde18e
topic_type:
- apiref
ms.openlocfilehash: 1ff2dd64dc4797bc485550c30f7204644a3adb47
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492274"
---
# <a name="imetadataimportenumfields-method"></a><span data-ttu-id="5a249-102">IMetaDataImport::EnumFields 方法</span><span class="sxs-lookup"><span data-stu-id="5a249-102">IMetaDataImport::EnumFields Method</span></span>
<span data-ttu-id="5a249-103">列舉指定 TypeDef 語彙基元所參考類型的 FieldDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="5a249-103">Enumerates FieldDef tokens for the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a249-104">語法</span><span class="sxs-lookup"><span data-stu-id="5a249-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFields (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   cl,
   [out]     mdFieldDef  rFields[],
   [in]      ULONG       cMax,
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a249-105">參數</span><span class="sxs-lookup"><span data-stu-id="5a249-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="5a249-106">[in、out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="5a249-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="5a249-107">在要列舉其欄位之類別的 TypeDef token。</span><span class="sxs-lookup"><span data-stu-id="5a249-107">[in] The TypeDef token of the class whose fields are to be enumerated.</span></span>  
  
 `rFields`  
 <span data-ttu-id="5a249-108">脫銷FieldDef token 的清單。</span><span class="sxs-lookup"><span data-stu-id="5a249-108">[out] The list of FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="5a249-109">[in] `rFields` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="5a249-109">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="5a249-110">脫銷在中傳回的 FieldDef token 實際數目 `rFields` 。</span><span class="sxs-lookup"><span data-stu-id="5a249-110">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a249-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="5a249-111">Return Value</span></span>  
  
|<span data-ttu-id="5a249-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5a249-112">HRESULT</span></span>|<span data-ttu-id="5a249-113">說明</span><span class="sxs-lookup"><span data-stu-id="5a249-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="5a249-114">`EnumFields`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="5a249-114">`EnumFields` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="5a249-115">沒有可列舉的欄位。</span><span class="sxs-lookup"><span data-stu-id="5a249-115">There are no fields to enumerate.</span></span> <span data-ttu-id="5a249-116">在此情況下， `pcTokens` 是零。</span><span class="sxs-lookup"><span data-stu-id="5a249-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5a249-117">規格需求</span><span class="sxs-lookup"><span data-stu-id="5a249-117">Requirements</span></span>  
 <span data-ttu-id="5a249-118">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5a249-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a249-119">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="5a249-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5a249-120">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5a249-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5a249-121">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a249-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a249-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a249-122">See also</span></span>

- [<span data-ttu-id="5a249-123">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="5a249-123">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="5a249-124">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="5a249-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
