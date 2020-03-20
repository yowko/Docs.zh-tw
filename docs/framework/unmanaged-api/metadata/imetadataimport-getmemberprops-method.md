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
ms.openlocfilehash: 72e14ea0414ebdeb8f54a4bdef8ce5208fc8ef72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177223"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="c36e1-102">IMetaDataImport::GetMemberProps 方法</span><span class="sxs-lookup"><span data-stu-id="c36e1-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="c36e1-103">獲取存儲在指定成員定義的中繼資料中的資訊，包括指定中繼資料權杖引用<xref:System.Type>的成員的名稱、二進位簽名和相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="c36e1-103">Gets information stored in the metadata for a specified member definition, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span> <span data-ttu-id="c36e1-104">這是一個簡單的説明方法：如果*mb*是一個方法Def，則調用**GetMethodProps;** 如果*mb*是 FieldDef，則調用**GetFieldProps。**</span><span class="sxs-lookup"><span data-stu-id="c36e1-104">This is a simple helper method: if *mb* is a MethodDef, then **GetMethodProps** is called; if *mb* is a FieldDef, then **GetFieldProps** is called.</span></span> <span data-ttu-id="c36e1-105">有關詳細資訊，請參閱這些其他方法。</span><span class="sxs-lookup"><span data-stu-id="c36e1-105">See these other methods for details.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="c36e1-106">語法</span><span class="sxs-lookup"><span data-stu-id="c36e1-106">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="c36e1-107">參數</span><span class="sxs-lookup"><span data-stu-id="c36e1-107">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="c36e1-108">[在]引用成員獲取關聯的中繼資料的權杖。</span><span class="sxs-lookup"><span data-stu-id="c36e1-108">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="c36e1-109">[出]指向表示成員類的中繼資料權杖的指標。</span><span class="sxs-lookup"><span data-stu-id="c36e1-109">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="c36e1-110">[出]成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="c36e1-110">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="c36e1-111">[在]`szMember`緩衝區的大小以寬字元表示。</span><span class="sxs-lookup"><span data-stu-id="c36e1-111">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="c36e1-112">[出]返回名稱的寬字元大小。</span><span class="sxs-lookup"><span data-stu-id="c36e1-112">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="c36e1-113">[出]應用於成員的任何標誌值。</span><span class="sxs-lookup"><span data-stu-id="c36e1-113">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="c36e1-114">[出]指向成員的二進位中繼資料簽名的指標。</span><span class="sxs-lookup"><span data-stu-id="c36e1-114">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="c36e1-115">[出]的大小（以位元組為單位）。 `ppvSigBlob`</span><span class="sxs-lookup"><span data-stu-id="c36e1-115">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="c36e1-116">[出]指向成員的相對虛擬位址的指標。</span><span class="sxs-lookup"><span data-stu-id="c36e1-116">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="c36e1-117">[出]與成員關聯的任何方法實現標誌。</span><span class="sxs-lookup"><span data-stu-id="c36e1-117">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="c36e1-118">[出]標記 的標誌<xref:System.ValueType>。</span><span class="sxs-lookup"><span data-stu-id="c36e1-118">[out] A flag that marks a <xref:System.ValueType>.</span></span> <span data-ttu-id="c36e1-119">它是`ELEMENT_TYPE_*`值之一。</span><span class="sxs-lookup"><span data-stu-id="c36e1-119">It is one of the `ELEMENT_TYPE_*` values.</span></span>
  
 `ppValue`  
 <span data-ttu-id="c36e1-120">[出]此成員返回的常量字串值。</span><span class="sxs-lookup"><span data-stu-id="c36e1-120">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="c36e1-121">[出]如果`ppValue`不保存字串，`ppValue`則以 字元或零表示的大小。</span><span class="sxs-lookup"><span data-stu-id="c36e1-121">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c36e1-122">需求</span><span class="sxs-lookup"><span data-stu-id="c36e1-122">Requirements</span></span>  
 <span data-ttu-id="c36e1-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c36e1-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c36e1-124">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="c36e1-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c36e1-125">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="c36e1-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c36e1-126">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c36e1-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c36e1-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c36e1-127">See also</span></span>

- [<span data-ttu-id="c36e1-128">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="c36e1-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="c36e1-129">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="c36e1-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
