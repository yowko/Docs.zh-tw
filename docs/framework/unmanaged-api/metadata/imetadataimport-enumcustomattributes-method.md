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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c38b7f060c34f7408195484dec2c49305db422fe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781313"
---
# <a name="imetadataimportenumcustomattributes-method"></a><span data-ttu-id="995ca-102">IMetaDataImport::EnumCustomAttributes 方法</span><span class="sxs-lookup"><span data-stu-id="995ca-102">IMetaDataImport::EnumCustomAttributes Method</span></span>
<span data-ttu-id="995ca-103">列舉指定的型別或成員相關聯的自訂屬性定義語彙基元。</span><span class="sxs-lookup"><span data-stu-id="995ca-103">Enumerates custom attribute-definition tokens associated with the specified type or member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="995ca-104">語法</span><span class="sxs-lookup"><span data-stu-id="995ca-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="995ca-105">參數</span><span class="sxs-lookup"><span data-stu-id="995ca-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="995ca-106">[in、 out]要傳回的列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="995ca-106">[in, out] A pointer to the returned enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="995ca-107">[in]語彙基元範圍的列舉型別或為零的所有自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="995ca-107">[in] A token for the scope of the enumeration, or zero for all custom attributes.</span></span>  
  
 `tkType`  
 <span data-ttu-id="995ca-108">[in]要列舉的屬性之型別的建構函式的語彙基元或`null`所有類型。</span><span class="sxs-lookup"><span data-stu-id="995ca-108">[in] A token for the constructor of the type of the attributes to be enumerated, or `null` for all types.</span></span>  
  
 `rCustomAttributes`  
 <span data-ttu-id="995ca-109">[out]自訂屬性的語彙基元的陣列。</span><span class="sxs-lookup"><span data-stu-id="995ca-109">[out] An array of custom attribute tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="995ca-110">[in] `rCustomAttributes` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="995ca-110">[in] The maximum size of the `rCustomAttributes` array.</span></span>  
  
 `pcCustomAttributes`  
 <span data-ttu-id="995ca-111">[out，optional]傳回的權杖值的實際數目`rCustomAttributes`。</span><span class="sxs-lookup"><span data-stu-id="995ca-111">[out, optional] The actual number of token values returned in `rCustomAttributes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="995ca-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="995ca-112">Return Value</span></span>  
  
|<span data-ttu-id="995ca-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="995ca-113">HRESULT</span></span>|<span data-ttu-id="995ca-114">描述</span><span class="sxs-lookup"><span data-stu-id="995ca-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="995ca-115">`EnumCustomAttributes` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="995ca-115">`EnumCustomAttributes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="995ca-116">沒有自訂屬性來列舉。</span><span class="sxs-lookup"><span data-stu-id="995ca-116">There are no custom attributes to enumerate.</span></span> <span data-ttu-id="995ca-117">在此情況下，`pcCustomAttributes`為零。</span><span class="sxs-lookup"><span data-stu-id="995ca-117">In that case, `pcCustomAttributes` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="995ca-118">需求</span><span class="sxs-lookup"><span data-stu-id="995ca-118">Requirements</span></span>  
 <span data-ttu-id="995ca-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="995ca-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="995ca-120">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="995ca-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="995ca-121">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="995ca-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="995ca-122">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="995ca-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="995ca-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="995ca-123">See also</span></span>

- [<span data-ttu-id="995ca-124">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="995ca-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="995ca-125">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="995ca-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
