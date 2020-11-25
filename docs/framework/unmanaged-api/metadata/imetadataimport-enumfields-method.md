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
ms.openlocfilehash: 74035e9551cb1d622b326e511c3884e1eadf057f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711581"
---
# <a name="imetadataimportenumfields-method"></a><span data-ttu-id="19fbf-102">IMetaDataImport::EnumFields 方法</span><span class="sxs-lookup"><span data-stu-id="19fbf-102">IMetaDataImport::EnumFields Method</span></span>

<span data-ttu-id="19fbf-103">列舉指定 TypeDef 語彙基元所參考類型的 FieldDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="19fbf-103">Enumerates FieldDef tokens for the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19fbf-104">語法</span><span class="sxs-lookup"><span data-stu-id="19fbf-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFields (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   cl,
   [out]     mdFieldDef  rFields[],
   [in]      ULONG       cMax,
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19fbf-105">參數</span><span class="sxs-lookup"><span data-stu-id="19fbf-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="19fbf-106">[in，out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="19fbf-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="19fbf-107">在要列舉其欄位之類別的 TypeDef 標記。</span><span class="sxs-lookup"><span data-stu-id="19fbf-107">[in] The TypeDef token of the class whose fields are to be enumerated.</span></span>  
  
 `rFields`  
 <span data-ttu-id="19fbf-108">擴展FieldDef token 的清單。</span><span class="sxs-lookup"><span data-stu-id="19fbf-108">[out] The list of FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="19fbf-109">[in] `rFields` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="19fbf-109">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="19fbf-110">擴展在中傳回的 FieldDef token 的實際數目 `rFields` 。</span><span class="sxs-lookup"><span data-stu-id="19fbf-110">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="19fbf-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="19fbf-111">Return Value</span></span>  
  
|<span data-ttu-id="19fbf-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="19fbf-112">HRESULT</span></span>|<span data-ttu-id="19fbf-113">描述</span><span class="sxs-lookup"><span data-stu-id="19fbf-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="19fbf-114">`EnumFields` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="19fbf-114">`EnumFields` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="19fbf-115">沒有可列舉的欄位。</span><span class="sxs-lookup"><span data-stu-id="19fbf-115">There are no fields to enumerate.</span></span> <span data-ttu-id="19fbf-116">在此情況下， `pcTokens` 是零。</span><span class="sxs-lookup"><span data-stu-id="19fbf-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="19fbf-117">需求</span><span class="sxs-lookup"><span data-stu-id="19fbf-117">Requirements</span></span>  

 <span data-ttu-id="19fbf-118">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="19fbf-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19fbf-119">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="19fbf-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="19fbf-120">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="19fbf-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="19fbf-121">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19fbf-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19fbf-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19fbf-122">See also</span></span>

- [<span data-ttu-id="19fbf-123">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="19fbf-123">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="19fbf-124">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="19fbf-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
