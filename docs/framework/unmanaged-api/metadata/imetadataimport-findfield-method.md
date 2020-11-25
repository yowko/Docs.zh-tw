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
ms.openlocfilehash: 9b42f0f7c8e2878ee3ec140344f51517a24247c4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729859"
---
# <a name="imetadataimportfindfield-method"></a><span data-ttu-id="880bc-102">IMetaDataImport::FindField 方法</span><span class="sxs-lookup"><span data-stu-id="880bc-102">IMetaDataImport::FindField Method</span></span>

<span data-ttu-id="880bc-103">取得欄位的 FieldDef token 指標，該欄位是由指定 <xref:System.Type> 且具有指定的名稱和中繼資料簽章的欄位所括住。</span><span class="sxs-lookup"><span data-stu-id="880bc-103">Gets a pointer to the FieldDef token for the field that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="880bc-104">語法</span><span class="sxs-lookup"><span data-stu-id="880bc-104">Syntax</span></span>  
  
```cpp  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="880bc-105">參數</span><span class="sxs-lookup"><span data-stu-id="880bc-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="880bc-106">在包含要搜尋之欄位的類別或介面的 TypeDef 標記。</span><span class="sxs-lookup"><span data-stu-id="880bc-106">[in] The TypeDef token for the class or interface that encloses the field to search for.</span></span> <span data-ttu-id="880bc-107">如果這個值為 `mdTokenNil` ，就會針對全域變數進行查閱。</span><span class="sxs-lookup"><span data-stu-id="880bc-107">If this value is `mdTokenNil`, the lookup is done for a global variable.</span></span>  
  
 `szName`  
 <span data-ttu-id="880bc-108">在要搜尋之欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="880bc-108">[in] The name of the field to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="880bc-109">在欄位的二進位中繼資料簽章指標。</span><span class="sxs-lookup"><span data-stu-id="880bc-109">[in] A pointer to the binary metadata signature of the field.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="880bc-110">在的大小（以位元組為單位） `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="880bc-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="880bc-111">擴展相符 FieldDef token 的指標。</span><span class="sxs-lookup"><span data-stu-id="880bc-111">[out] A pointer to the matching FieldDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="880bc-112">備註</span><span class="sxs-lookup"><span data-stu-id="880bc-112">Remarks</span></span>  

 <span data-ttu-id="880bc-113">您可以使用其封入類別或介面 (`td`) 、其名稱 (`szName`) ，以及選擇性的簽章 () ，來指定欄位 `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="880bc-113">You specify the field using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="880bc-114">傳遞給的簽章 `FindField` 必須在目前的範圍內產生，因為簽章會系結至特定的範圍。</span><span class="sxs-lookup"><span data-stu-id="880bc-114">The signature passed to `FindField` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="880bc-115">簽章可以內嵌可識別封閉類別或實數值型別的標記。</span><span class="sxs-lookup"><span data-stu-id="880bc-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="880bc-116"> (權杖是) 的本機 TypeDef 資料表的索引。</span><span class="sxs-lookup"><span data-stu-id="880bc-116">(The token is an index into the local TypeDef table).</span></span> <span data-ttu-id="880bc-117">您無法在目前範圍的內容之外建立執行時間簽章，並使用該簽章做為的輸入 `FindField` 。</span><span class="sxs-lookup"><span data-stu-id="880bc-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindField`.</span></span>  
  
 <span data-ttu-id="880bc-118">`FindField` 只尋找直接在類別或介面中定義的欄位;找不到繼承的欄位。</span><span class="sxs-lookup"><span data-stu-id="880bc-118">`FindField` finds only fields that were defined directly in the class or interface; it does not find inherited fields.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="880bc-119">需求</span><span class="sxs-lookup"><span data-stu-id="880bc-119">Requirements</span></span>  

 <span data-ttu-id="880bc-120">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="880bc-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="880bc-121">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="880bc-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="880bc-122">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="880bc-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="880bc-123">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="880bc-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="880bc-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="880bc-124">See also</span></span>

- [<span data-ttu-id="880bc-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="880bc-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="880bc-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="880bc-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
