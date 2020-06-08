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
ms.openlocfilehash: 0357444aa8fa38bce5a7175cf6aacfe1a2b2b16e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503636"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="83899-102">IMetaDataImport::GetMemberProps 方法</span><span class="sxs-lookup"><span data-stu-id="83899-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="83899-103">取得儲存在指定之元資料標記所參考之成員的中繼資料中的資訊（包括名稱、二進位簽章和相對虛擬位址） <xref:System.Type> 。</span><span class="sxs-lookup"><span data-stu-id="83899-103">Gets information stored in the metadata for a specified member definition, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span> <span data-ttu-id="83899-104">這是簡單的 helper 方法：如果*mb*是 MethodDef，則會呼叫**GetMethodProps** ;如果*mb*是 FieldDef，則會呼叫**GetFieldProps** 。</span><span class="sxs-lookup"><span data-stu-id="83899-104">This is a simple helper method: if *mb* is a MethodDef, then **GetMethodProps** is called; if *mb* is a FieldDef, then **GetFieldProps** is called.</span></span> <span data-ttu-id="83899-105">如需詳細資訊，請參閱這些其他方法。</span><span class="sxs-lookup"><span data-stu-id="83899-105">See these other methods for details.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="83899-106">語法</span><span class="sxs-lookup"><span data-stu-id="83899-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="83899-107">參數</span><span class="sxs-lookup"><span data-stu-id="83899-107">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="83899-108">在參考要取得相關聯中繼資料之成員的 token。</span><span class="sxs-lookup"><span data-stu-id="83899-108">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="83899-109">脫銷元資料標記的指標，表示成員的類別。</span><span class="sxs-lookup"><span data-stu-id="83899-109">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="83899-110">脫銷成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="83899-110">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="83899-111">在緩衝區的大小（以寬字元為單位） `szMember` 。</span><span class="sxs-lookup"><span data-stu-id="83899-111">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="83899-112">脫銷傳回名稱的大小（以寬字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="83899-112">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="83899-113">脫銷套用至成員的任何旗標值。</span><span class="sxs-lookup"><span data-stu-id="83899-113">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="83899-114">脫銷成員的二進位中繼資料簽章的指標。</span><span class="sxs-lookup"><span data-stu-id="83899-114">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="83899-115">脫銷的大小（以位元組為單位） `ppvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="83899-115">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="83899-116">脫銷成員之相對虛擬位址的指標。</span><span class="sxs-lookup"><span data-stu-id="83899-116">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="83899-117">脫銷與成員相關聯的任何方法執行旗標。</span><span class="sxs-lookup"><span data-stu-id="83899-117">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="83899-118">脫銷標記的旗標 <xref:System.ValueType> 。</span><span class="sxs-lookup"><span data-stu-id="83899-118">[out] A flag that marks a <xref:System.ValueType>.</span></span> <span data-ttu-id="83899-119">它是其中一個 `ELEMENT_TYPE_*` 值。</span><span class="sxs-lookup"><span data-stu-id="83899-119">It is one of the `ELEMENT_TYPE_*` values.</span></span>
  
 `ppValue`  
 <span data-ttu-id="83899-120">脫銷這個成員傳回的常數位串值。</span><span class="sxs-lookup"><span data-stu-id="83899-120">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="83899-121">脫銷的大小（以字元為單位 `ppValue` ），如果不包含字串，則為零 `ppValue` 。</span><span class="sxs-lookup"><span data-stu-id="83899-121">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83899-122">規格需求</span><span class="sxs-lookup"><span data-stu-id="83899-122">Requirements</span></span>  
 <span data-ttu-id="83899-123">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="83899-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83899-124">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="83899-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="83899-125">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="83899-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="83899-126">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83899-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83899-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83899-127">See also</span></span>

- [<span data-ttu-id="83899-128">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="83899-128">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="83899-129">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="83899-129">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
