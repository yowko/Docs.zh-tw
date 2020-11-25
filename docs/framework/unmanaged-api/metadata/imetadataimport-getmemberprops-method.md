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
ms.openlocfilehash: f01d65a339c77e6af3e768c620f17ef0190c1e58
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733213"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="2b089-102">IMetaDataImport::GetMemberProps 方法</span><span class="sxs-lookup"><span data-stu-id="2b089-102">IMetaDataImport::GetMemberProps Method</span></span>

<span data-ttu-id="2b089-103">針對指定的元資料標記所參考的成員，取得儲存在中繼資料中的指定成員定義，包括名稱、二進位簽章和相對虛擬位址 <xref:System.Type> 。</span><span class="sxs-lookup"><span data-stu-id="2b089-103">Gets information stored in the metadata for a specified member definition, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span> <span data-ttu-id="2b089-104">這是簡單的 helper 方法：如果有 *mb* 是 MethodDef，則會呼叫 **GetMethodProps** ;如果 *mb* 是 FieldDef，則會呼叫 **GetFieldProps** 。</span><span class="sxs-lookup"><span data-stu-id="2b089-104">This is a simple helper method: if *mb* is a MethodDef, then **GetMethodProps** is called; if *mb* is a FieldDef, then **GetFieldProps** is called.</span></span> <span data-ttu-id="2b089-105">如需詳細資訊，請參閱這些其他方法。</span><span class="sxs-lookup"><span data-stu-id="2b089-105">See these other methods for details.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="2b089-106">語法</span><span class="sxs-lookup"><span data-stu-id="2b089-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="2b089-107">參數</span><span class="sxs-lookup"><span data-stu-id="2b089-107">Parameters</span></span>  

 `mb`  
 <span data-ttu-id="2b089-108">在參考成員以取得相關聯中繼資料的權杖。</span><span class="sxs-lookup"><span data-stu-id="2b089-108">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="2b089-109">擴展元資料標記的指標，表示成員的類別。</span><span class="sxs-lookup"><span data-stu-id="2b089-109">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="2b089-110">擴展成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="2b089-110">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="2b089-111">在緩衝區的大小（以寬字元為單位） `szMember` 。</span><span class="sxs-lookup"><span data-stu-id="2b089-111">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="2b089-112">擴展傳回名稱的大小（以寬字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="2b089-112">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="2b089-113">擴展套用至成員的任何旗標值。</span><span class="sxs-lookup"><span data-stu-id="2b089-113">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="2b089-114">擴展成員的二進位中繼資料簽章指標。</span><span class="sxs-lookup"><span data-stu-id="2b089-114">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="2b089-115">擴展的大小（以位元組為單位） `ppvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="2b089-115">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="2b089-116">擴展成員之相對虛擬位址的指標。</span><span class="sxs-lookup"><span data-stu-id="2b089-116">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="2b089-117">擴展與成員相關聯的任何方法執行旗標。</span><span class="sxs-lookup"><span data-stu-id="2b089-117">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="2b089-118">擴展標記的旗標 <xref:System.ValueType> 。</span><span class="sxs-lookup"><span data-stu-id="2b089-118">[out] A flag that marks a <xref:System.ValueType>.</span></span> <span data-ttu-id="2b089-119">這是其中一個 `ELEMENT_TYPE_*` 值。</span><span class="sxs-lookup"><span data-stu-id="2b089-119">It is one of the `ELEMENT_TYPE_*` values.</span></span>
  
 `ppValue`  
 <span data-ttu-id="2b089-120">擴展這個成員所傳回的常數位串值。</span><span class="sxs-lookup"><span data-stu-id="2b089-120">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="2b089-121">擴展的大小（以字元為單位 `ppValue` ），如果不包含字串，則為零 `ppValue` 。</span><span class="sxs-lookup"><span data-stu-id="2b089-121">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b089-122">需求</span><span class="sxs-lookup"><span data-stu-id="2b089-122">Requirements</span></span>  

 <span data-ttu-id="2b089-123">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2b089-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b089-124">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="2b089-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2b089-125">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="2b089-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2b089-126">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b089-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b089-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b089-127">See also</span></span>

- [<span data-ttu-id="2b089-128">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="2b089-128">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="2b089-129">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="2b089-129">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
