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
ms.openlocfilehash: c27a55166ebc055f324ec45ba6dfd835c8b8bbf6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075739"
---
# <a name="imetadataimportgetcustomattributeprops-method"></a><span data-ttu-id="23cab-102">IMetaDataImport::GetCustomAttributeProps 方法</span><span class="sxs-lookup"><span data-stu-id="23cab-102">IMetaDataImport::GetCustomAttributeProps Method</span></span>
<span data-ttu-id="23cab-103">根據提供的中繼資料語彙基元，取得自訂屬性的值。</span><span class="sxs-lookup"><span data-stu-id="23cab-103">Gets the value of the custom attribute, given its metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23cab-104">語法</span><span class="sxs-lookup"><span data-stu-id="23cab-104">Syntax</span></span>  
  
```  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23cab-105">參數</span><span class="sxs-lookup"><span data-stu-id="23cab-105">Parameters</span></span>  
 `cv`  
 <span data-ttu-id="23cab-106">[in] 中繼資料語彙基元，代表要擷取的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="23cab-106">[in] A metadata token that represents the custom attribute to be retrieved.</span></span>  
  
 `ptkObj`  
 <span data-ttu-id="23cab-107">[out, optional] 中繼資料語彙基元，代表自訂屬性修改的物件。</span><span class="sxs-lookup"><span data-stu-id="23cab-107">[out, optional] A metadata token representing the object that the custom attribute modifies.</span></span> <span data-ttu-id="23cab-108">這個值可以是 `mdCustomAttribute` 以外之任何類型的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="23cab-108">This value can be any type of metadata token except `mdCustomAttribute`.</span></span>  
  
 `ptkType`  
 <span data-ttu-id="23cab-109">[out, optional] `mdMethodDef` 或 `mdMemberRef` 中繼資料語彙基元，代表所傳回之自訂屬性的 <xref:System.Type>。</span><span class="sxs-lookup"><span data-stu-id="23cab-109">[out, optional] An `mdMethodDef` or `mdMemberRef` metadata token representing the <xref:System.Type> of the returned custom attribute.</span></span>  
  
 `ppBlob`  
 <span data-ttu-id="23cab-110">[out, optional] 做為自訂屬性值之資料陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="23cab-110">[out, optional] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="23cab-111">[out, optional] `ppBlob` 中傳回之資料的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="23cab-111">[out, optional] The size in bytes of the data returned in \*`ppBlob`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23cab-112">備註</span><span class="sxs-lookup"><span data-stu-id="23cab-112">Remarks</span></span>  
 <span data-ttu-id="23cab-113">自訂屬性會儲存為資料陣列，這是中繼資料引擎了解的格式。</span><span class="sxs-lookup"><span data-stu-id="23cab-113">A custom attribute is stored as an array of data, the format which is understood by the metadata engine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23cab-114">需求</span><span class="sxs-lookup"><span data-stu-id="23cab-114">Requirements</span></span>  
 <span data-ttu-id="23cab-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="23cab-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23cab-116">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="23cab-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="23cab-117">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="23cab-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="23cab-118">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="23cab-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="23cab-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23cab-119">See also</span></span>

- [<span data-ttu-id="23cab-120">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="23cab-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="23cab-121">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="23cab-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
