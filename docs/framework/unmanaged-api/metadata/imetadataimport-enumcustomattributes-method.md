---
title: IMetaDataImport::EnumCustomAttributes 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumCustomAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method [.NET Framework metadata]
- IMetaDataImport::EnumCustomAttributes method [.NET Framework metadata]
ms.assetid: 798513a0-68b1-4d04-bc5b-782a4445ea68
topic_type:
- apiref
ms.openlocfilehash: 3b12200dae23a7b6a2f6e1654e46fdf74dc90968
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700531"
---
# <a name="imetadataimportenumcustomattributes-method"></a><span data-ttu-id="9073b-102">IMetaDataImport::EnumCustomAttributes 方法</span><span class="sxs-lookup"><span data-stu-id="9073b-102">IMetaDataImport::EnumCustomAttributes Method</span></span>

<span data-ttu-id="9073b-103">列舉與指定類型或成員相關聯的自訂屬性定義標記。</span><span class="sxs-lookup"><span data-stu-id="9073b-103">Enumerates custom attribute-definition tokens associated with the specified type or member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9073b-104">語法</span><span class="sxs-lookup"><span data-stu-id="9073b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes (
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,
   [in]  mdToken            tkType,
   [out] mdCustomAttribute  rCustomAttributes[],
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9073b-105">參數</span><span class="sxs-lookup"><span data-stu-id="9073b-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="9073b-106">[in，out]傳回之列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="9073b-106">[in, out] A pointer to the returned enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="9073b-107">在列舉範圍的標記，或所有自訂屬性為零。</span><span class="sxs-lookup"><span data-stu-id="9073b-107">[in] A token for the scope of the enumeration, or zero for all custom attributes.</span></span>  
  
 `tkType`  
 <span data-ttu-id="9073b-108">在要列舉之屬性類型的函式或 `null` 所有類型的標記。</span><span class="sxs-lookup"><span data-stu-id="9073b-108">[in] A token for the constructor of the type of the attributes to be enumerated, or `null` for all types.</span></span>  
  
 `rCustomAttributes`  
 <span data-ttu-id="9073b-109">擴展自訂屬性標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="9073b-109">[out] An array of custom attribute tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="9073b-110">[in] `rCustomAttributes` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="9073b-110">[in] The maximum size of the `rCustomAttributes` array.</span></span>  
  
 `pcCustomAttributes`  
 <span data-ttu-id="9073b-111">[out，optional]中傳回的實際 token 值數目 `rCustomAttributes` 。</span><span class="sxs-lookup"><span data-stu-id="9073b-111">[out, optional] The actual number of token values returned in `rCustomAttributes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9073b-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="9073b-112">Return Value</span></span>  
  
|<span data-ttu-id="9073b-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9073b-113">HRESULT</span></span>|<span data-ttu-id="9073b-114">描述</span><span class="sxs-lookup"><span data-stu-id="9073b-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="9073b-115">`EnumCustomAttributes` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="9073b-115">`EnumCustomAttributes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="9073b-116">沒有要列舉的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="9073b-116">There are no custom attributes to enumerate.</span></span> <span data-ttu-id="9073b-117">在此情況下， `pcCustomAttributes` 是零。</span><span class="sxs-lookup"><span data-stu-id="9073b-117">In that case, `pcCustomAttributes` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9073b-118">需求</span><span class="sxs-lookup"><span data-stu-id="9073b-118">Requirements</span></span>  

 <span data-ttu-id="9073b-119">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9073b-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9073b-120">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="9073b-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9073b-121">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="9073b-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9073b-122">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9073b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9073b-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9073b-123">See also</span></span>

- [<span data-ttu-id="9073b-124">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="9073b-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="9073b-125">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="9073b-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
