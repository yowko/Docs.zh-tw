---
title: IMetaDataImport::FindField 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindField
helpviewer_keywords:
- IMetaDataImport::FindField method [.NET Framework metadata]
- FindField method [.NET Framework metadata]
ms.assetid: 38cd4e16-fbb2-471c-aa73-ac51a1931ad2
topic_type:
- apiref
ms.openlocfilehash: 11ea6e468909ea42e38bdc7b76c60c460c98025e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503662"
---
# <a name="imetadataimportfindfield-method"></a><span data-ttu-id="d0798-102">IMetaDataImport::FindField 方法</span><span class="sxs-lookup"><span data-stu-id="d0798-102">IMetaDataImport::FindField Method</span></span>
<span data-ttu-id="d0798-103">取得欄位的 FieldDef token 指標，此標記是由指定的所括住， <xref:System.Type> 且具有指定的名稱和中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="d0798-103">Gets a pointer to the FieldDef token for the field that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0798-104">語法</span><span class="sxs-lookup"><span data-stu-id="d0798-104">Syntax</span></span>  
  
```cpp  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0798-105">參數</span><span class="sxs-lookup"><span data-stu-id="d0798-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="d0798-106">在用來括住要搜尋之欄位的類別或介面的 TypeDef token。</span><span class="sxs-lookup"><span data-stu-id="d0798-106">[in] The TypeDef token for the class or interface that encloses the field to search for.</span></span> <span data-ttu-id="d0798-107">如果這個值為 `mdTokenNil` ，則會針對全域變數進行查閱。</span><span class="sxs-lookup"><span data-stu-id="d0798-107">If this value is `mdTokenNil`, the lookup is done for a global variable.</span></span>  
  
 `szName`  
 <span data-ttu-id="d0798-108">在要搜尋之欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="d0798-108">[in] The name of the field to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="d0798-109">在欄位的二進位中繼資料簽章的指標。</span><span class="sxs-lookup"><span data-stu-id="d0798-109">[in] A pointer to the binary metadata signature of the field.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="d0798-110">在的大小（以位元組為單位） `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="d0798-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="d0798-111">脫銷對應之 FieldDef token 的指標。</span><span class="sxs-lookup"><span data-stu-id="d0798-111">[out] A pointer to the matching FieldDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0798-112">備註</span><span class="sxs-lookup"><span data-stu-id="d0798-112">Remarks</span></span>  
 <span data-ttu-id="d0798-113">您可以使用其封入類別或介面（ `td` ）、其名稱（） `szName` ，以及選擇性的簽章（）來指定欄位 `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="d0798-113">You specify the field using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="d0798-114">傳遞至的簽章 `FindField` 必須已在目前的範圍中產生，因為簽章已系結至特定範圍。</span><span class="sxs-lookup"><span data-stu-id="d0798-114">The signature passed to `FindField` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="d0798-115">簽章可以內嵌可識別封閉類別或實數值型別的 token。</span><span class="sxs-lookup"><span data-stu-id="d0798-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="d0798-116">（Token 是本機 TypeDef 資料表的索引）。</span><span class="sxs-lookup"><span data-stu-id="d0798-116">(The token is an index into the local TypeDef table).</span></span> <span data-ttu-id="d0798-117">您無法在目前範圍的內容之外建立執行時間簽章，並使用該簽章做為的輸入 `FindField` 。</span><span class="sxs-lookup"><span data-stu-id="d0798-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindField`.</span></span>  
  
 <span data-ttu-id="d0798-118">`FindField`只尋找直接定義于類別或介面中的欄位;它找不到繼承的欄位。</span><span class="sxs-lookup"><span data-stu-id="d0798-118">`FindField` finds only fields that were defined directly in the class or interface; it does not find inherited fields.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0798-119">規格需求</span><span class="sxs-lookup"><span data-stu-id="d0798-119">Requirements</span></span>  
 <span data-ttu-id="d0798-120">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d0798-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0798-121">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="d0798-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d0798-122">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d0798-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d0798-123">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0798-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0798-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0798-124">See also</span></span>

- [<span data-ttu-id="d0798-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="d0798-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="d0798-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="d0798-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
