---
title: IMetaDataImport::GetCustomAttributeProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetCustomAttributeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeProps
helpviewer_keywords:
- GetCustomAttributeProps method [.NET Framework metadata]
- IMetaDataImport::GetCustomAttributeProps method [.NET Framework metadata]
ms.assetid: 6eefb243-a281-41c1-bcdc-7e17513bc446
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a4ed21b6f9fd067f3357e07c5fda07d25ce868d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448399"
---
# <a name="imetadataimportgetcustomattributeprops-method"></a><span data-ttu-id="65714-102">IMetaDataImport::GetCustomAttributeProps 方法</span><span class="sxs-lookup"><span data-stu-id="65714-102">IMetaDataImport::GetCustomAttributeProps Method</span></span>
<span data-ttu-id="65714-103">根據提供的中繼資料語彙基元，取得自訂屬性的值。</span><span class="sxs-lookup"><span data-stu-id="65714-103">Gets the value of the custom attribute, given its metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65714-104">語法</span><span class="sxs-lookup"><span data-stu-id="65714-104">Syntax</span></span>  
  
```  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="65714-105">參數</span><span class="sxs-lookup"><span data-stu-id="65714-105">Parameters</span></span>  
 `cv`  
 <span data-ttu-id="65714-106">[in] 中繼資料語彙基元，代表要擷取的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="65714-106">[in] A metadata token that represents the custom attribute to be retrieved.</span></span>  
  
 `ptkObj`  
 <span data-ttu-id="65714-107">[out, optional] 中繼資料語彙基元，代表自訂屬性修改的物件。</span><span class="sxs-lookup"><span data-stu-id="65714-107">[out, optional] A metadata token representing the object that the custom attribute modifies.</span></span> <span data-ttu-id="65714-108">這個值可以是 `mdCustomAttribute` 以外之任何類型的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="65714-108">This value can be any type of metadata token except `mdCustomAttribute`.</span></span>  
  
 `ptkType`  
 <span data-ttu-id="65714-109">[out, optional] `mdMethodDef` 或 `mdMemberRef` 中繼資料語彙基元，代表所傳回之自訂屬性的 <xref:System.Type>。</span><span class="sxs-lookup"><span data-stu-id="65714-109">[out, optional] An `mdMethodDef` or `mdMemberRef` metadata token representing the <xref:System.Type> of the returned custom attribute.</span></span>  
  
 `ppBlob`  
 <span data-ttu-id="65714-110">[out, optional] 做為自訂屬性值之資料陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="65714-110">[out, optional] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="65714-111">[out, optional] `ppBlob` 中傳回之資料的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="65714-111">[out, optional] The size in bytes of the data returned in \*`ppBlob`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65714-112">備註</span><span class="sxs-lookup"><span data-stu-id="65714-112">Remarks</span></span>  
 <span data-ttu-id="65714-113">自訂屬性會儲存為資料陣列，這是中繼資料引擎了解的格式。</span><span class="sxs-lookup"><span data-stu-id="65714-113">A custom attribute is stored as an array of data, the format which is understood by the metadata engine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65714-114">需求</span><span class="sxs-lookup"><span data-stu-id="65714-114">Requirements</span></span>  
 <span data-ttu-id="65714-115">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="65714-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65714-116">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="65714-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="65714-117">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="65714-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="65714-118">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65714-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65714-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65714-119">See Also</span></span>  
 [<span data-ttu-id="65714-120">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="65714-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="65714-121">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="65714-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
