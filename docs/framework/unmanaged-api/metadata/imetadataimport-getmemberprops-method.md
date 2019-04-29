---
title: IMetaDataImport::GetMemberProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberProps
helpviewer_keywords:
- IMetaDataImport::GetMemberProps method [.NET Framework metadata]
- GetMemberProps method [.NET Framework metadata]
ms.assetid: 42790918-4142-4938-b8f4-a56979a55846
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83dec9b6ed3b1e538e0f1b7d13a33b8bdbc1cf54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777724"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="b10e1-102">IMetaDataImport::GetMemberProps 方法</span><span class="sxs-lookup"><span data-stu-id="b10e1-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="b10e1-103">取得儲存在指定的成員定義，包括名稱、 二進位簽章和相對虛擬位址的中繼資料中的資訊<xref:System.Type>指定之中繼資料語彙基元所參考的成員。</span><span class="sxs-lookup"><span data-stu-id="b10e1-103">Gets information stored in the metadata for a specified member definition, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span> <span data-ttu-id="b10e1-104">這是一個簡單的 helper 方法： 如果*mb*就的 MethodDef **GetMethodProps**呼叫; 如果*mb*就的 fielddef 語彙**GetFieldProps**會呼叫。</span><span class="sxs-lookup"><span data-stu-id="b10e1-104">This is a simple helper method: if *mb* is a MethodDef, then **GetMethodProps** is called; if *mb* is a FieldDef, then **GetFieldProps** is called.</span></span> <span data-ttu-id="b10e1-105">請參閱這些其他方法，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="b10e1-105">See these other methods for details.</span></span> 
  
## <a name="syntax"></a><span data-ttu-id="b10e1-106">語法</span><span class="sxs-lookup"><span data-stu-id="b10e1-106">Syntax</span></span>  
  
```  
HRESULT GetMemberProps (  
   [in]  mdToken           mb,   
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szMember,   
   [in]  ULONG             cchMember,   
   [out] ULONG             *pchMember,   
   [out] DWORD             *pdwAttr,  
   [out] PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pcbSigBlob,   
   [out] ULONG             *pulCodeRVA,   
   [out] DWORD             *pdwImplFlags,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b10e1-107">參數</span><span class="sxs-lookup"><span data-stu-id="b10e1-107">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="b10e1-108">[in]參考的成員，以取得相關聯中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b10e1-108">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="b10e1-109">[out]表示的類別成員的中繼資料語彙基元指標。</span><span class="sxs-lookup"><span data-stu-id="b10e1-109">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="b10e1-110">[out]成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="b10e1-110">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="b10e1-111">[in]寬字元大小`szMember`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="b10e1-111">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="b10e1-112">[out]寬字元，傳回的檔案名稱的大小。</span><span class="sxs-lookup"><span data-stu-id="b10e1-112">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="b10e1-113">[out]任何旗標套用至成員的值。</span><span class="sxs-lookup"><span data-stu-id="b10e1-113">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="b10e1-114">[out]二進位中繼資料簽章的成員指標。</span><span class="sxs-lookup"><span data-stu-id="b10e1-114">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="b10e1-115">[out]以位元組為單位的大小`ppvSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="b10e1-115">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="b10e1-116">[out]成員的相對虛擬位址指標。</span><span class="sxs-lookup"><span data-stu-id="b10e1-116">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="b10e1-117">[out]成員相關聯任何方法實作旗標。</span><span class="sxs-lookup"><span data-stu-id="b10e1-117">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="b10e1-118">[out]標示旗標<xref:System.ValueType>。</span><span class="sxs-lookup"><span data-stu-id="b10e1-118">[out] A flag that marks a <xref:System.ValueType>.</span></span> <span data-ttu-id="b10e1-119">它是其中一個`ELEMENT_TYPE_*`值。</span><span class="sxs-lookup"><span data-stu-id="b10e1-119">It is one of the `ELEMENT_TYPE_*` values.</span></span>
  
 `ppValue`  
 <span data-ttu-id="b10e1-120">[out]常數字串值，這個成員所傳回。</span><span class="sxs-lookup"><span data-stu-id="b10e1-120">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="b10e1-121">[out]以字元為單位的大小`ppValue`，或零，如果`ppValue`不會保留為字串。</span><span class="sxs-lookup"><span data-stu-id="b10e1-121">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b10e1-122">需求</span><span class="sxs-lookup"><span data-stu-id="b10e1-122">Requirements</span></span>  
 <span data-ttu-id="b10e1-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b10e1-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b10e1-124">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b10e1-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b10e1-125">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b10e1-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b10e1-126">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b10e1-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b10e1-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b10e1-127">See also</span></span>

- [<span data-ttu-id="b10e1-128">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="b10e1-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b10e1-129">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="b10e1-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
