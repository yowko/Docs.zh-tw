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
ms.openlocfilehash: 8c3f98a124dbbcae3b0500932a2357ed1757951f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177239"
---
# <a name="imetadataimportgetfieldprops-method"></a><span data-ttu-id="66601-102">IMetaDataImport::GetFieldProps 方法</span><span class="sxs-lookup"><span data-stu-id="66601-102">IMetaDataImport::GetFieldProps Method</span></span>
<span data-ttu-id="66601-103">取得與指定 FieldDef 語彙基元所參考欄位相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="66601-103">Gets metadata associated with the field referenced by the specified FieldDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66601-104">語法</span><span class="sxs-lookup"><span data-stu-id="66601-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="66601-105">參數</span><span class="sxs-lookup"><span data-stu-id="66601-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="66601-106">[在]表示要為其獲取關聯的中繼資料的欄位的 FieldDef 權杖。</span><span class="sxs-lookup"><span data-stu-id="66601-106">[in] A FieldDef token that represents the field to get associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="66601-107">[出]指向 TypeDef 權杖的指標，表示欄位所屬的類的類型。</span><span class="sxs-lookup"><span data-stu-id="66601-107">[out] A pointer to a TypeDef token that represents the type of the class that the field belongs to.</span></span>  
  
 `szField`  
 <span data-ttu-id="66601-108">[出]欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="66601-108">[out] The name of the field.</span></span>  
  
 `cchField`  
 <span data-ttu-id="66601-109">[在]*szField*緩衝區的大小以寬字元表示。</span><span class="sxs-lookup"><span data-stu-id="66601-109">[in] The size in wide characters of the buffer for *szField*.</span></span>  
  
 `pchField`  
 <span data-ttu-id="66601-110">[出]返回的緩衝區的實際大小。</span><span class="sxs-lookup"><span data-stu-id="66601-110">[out] The actual size of the returned buffer.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="66601-111">[出]與欄位的中繼資料關聯的標誌。</span><span class="sxs-lookup"><span data-stu-id="66601-111">[out] Flags associated with the field's metadata.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="66601-112">[在]指向描述欄位的二進位中繼資料值的指標。</span><span class="sxs-lookup"><span data-stu-id="66601-112">[in] A pointer to the binary metadata value that describes the field.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="66601-113">[出]的大小（以位元組為單位）。 `ppvSigBlob`</span><span class="sxs-lookup"><span data-stu-id="66601-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="66601-114">[出]指定欄位的數值型別的標誌。</span><span class="sxs-lookup"><span data-stu-id="66601-114">[out] A flag that specifies the value type of the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="66601-115">[出]欄位的常量值。</span><span class="sxs-lookup"><span data-stu-id="66601-115">[out] A constant value for the field.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="66601-116">[出]如果不存在字串，則大小`ppValue`以 的 字元表示或零。</span><span class="sxs-lookup"><span data-stu-id="66601-116">[out] The size in chars of `ppValue`, or zero if no string exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66601-117">需求</span><span class="sxs-lookup"><span data-stu-id="66601-117">Requirements</span></span>  
 <span data-ttu-id="66601-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="66601-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66601-119">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="66601-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="66601-120">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="66601-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="66601-121">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66601-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66601-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66601-122">See also</span></span>

- [<span data-ttu-id="66601-123">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="66601-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="66601-124">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="66601-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
