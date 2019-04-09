---
title: IMetaDataImport::GetFieldProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldProps
helpviewer_keywords:
- IMetaDataImport::GetFieldProps method [.NET Framework metadata]
- GetFieldProps method [.NET Framework metadata]
ms.assetid: 7b0e9b10-8cef-4ba6-8432-40bf63e65ab1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d7f8cccf8d583645982eb37f6afcb553914679ad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075655"
---
# <a name="imetadataimportgetfieldprops-method"></a><span data-ttu-id="68807-102">IMetaDataImport::GetFieldProps 方法</span><span class="sxs-lookup"><span data-stu-id="68807-102">IMetaDataImport::GetFieldProps Method</span></span>
<span data-ttu-id="68807-103">取得與指定 FieldDef 語彙基元所參考欄位相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="68807-103">Gets metadata associated with the field referenced by the specified FieldDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68807-104">語法</span><span class="sxs-lookup"><span data-stu-id="68807-104">Syntax</span></span>  
  
```  
HRESULT GetFieldProps (  
   [in]  mdFieldDef        mb,   
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szField,  
   [in]  ULONG             cchField,   
   [out] ULONG             *pchField,  
   [out] DWORD             *pdwAttr,  
   [in]  PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pcbSigBlob,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68807-105">參數</span><span class="sxs-lookup"><span data-stu-id="68807-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="68807-106">[in]FieldDef 語彙基元，表示要取得相關聯的中繼資料的欄位。</span><span class="sxs-lookup"><span data-stu-id="68807-106">[in] A FieldDef token that represents the field to get associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="68807-107">[out]表示欄位所屬的類別類型的 TypeDef 語彙基元指標。</span><span class="sxs-lookup"><span data-stu-id="68807-107">[out] A pointer to a TypeDef token that represents the type of the class that the field belongs to.</span></span>  
  
 `szField`  
 <span data-ttu-id="68807-108">[out]欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="68807-108">[out] The name of the field.</span></span>  
  
 `cchField`  
 <span data-ttu-id="68807-109">[in]寬字元緩衝區的大小*szField*。</span><span class="sxs-lookup"><span data-stu-id="68807-109">[in] The size in wide characters of the buffer for *szField*.</span></span>  
  
 `pchField`  
 <span data-ttu-id="68807-110">[out]傳回的緩衝區實際大小。</span><span class="sxs-lookup"><span data-stu-id="68807-110">[out] The actual size of the returned buffer.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="68807-111">[out]欄位的中繼資料相關聯的旗標。</span><span class="sxs-lookup"><span data-stu-id="68807-111">[out] Flags associated with the field's metadata.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="68807-112">[in]描述欄位的二進位中繼資料值的指標。</span><span class="sxs-lookup"><span data-stu-id="68807-112">[in] A pointer to the binary metadata value that describes the field.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="68807-113">[out]以位元組為單位的大小`ppvSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="68807-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="68807-114">[out]指定欄位的值類型的旗標。</span><span class="sxs-lookup"><span data-stu-id="68807-114">[out] A flag that specifies the value type of the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="68807-115">[out]欄位的常值。</span><span class="sxs-lookup"><span data-stu-id="68807-115">[out] A constant value for the field.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="68807-116">[out]以字元為單位的大小`ppValue`，零，如果不有任何字串。</span><span class="sxs-lookup"><span data-stu-id="68807-116">[out] The size in chars of `ppValue`, or zero if no string exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68807-117">需求</span><span class="sxs-lookup"><span data-stu-id="68807-117">Requirements</span></span>  
 <span data-ttu-id="68807-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="68807-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68807-119">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="68807-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="68807-120">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="68807-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="68807-121">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="68807-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="68807-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68807-122">See also</span></span>

- [<span data-ttu-id="68807-123">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="68807-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="68807-124">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="68807-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
