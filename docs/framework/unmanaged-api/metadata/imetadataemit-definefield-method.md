---
title: IMetaDataEmit::DefineField 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type:
- apiref
ms.openlocfilehash: 2bc2b983171dc41d5ac37eda0359f1aaee4ebd6e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725751"
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="7de44-102">IMetaDataEmit::DefineField 方法</span><span class="sxs-lookup"><span data-stu-id="7de44-102">IMetaDataEmit::DefineField Method</span></span>

<span data-ttu-id="7de44-103">使用指定的中繼資料簽章建立欄位的定義，並取得該欄位定義的標記。</span><span class="sxs-lookup"><span data-stu-id="7de44-103">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7de44-104">語法</span><span class="sxs-lookup"><span data-stu-id="7de44-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineField (
    [in]  mdTypeDef   td,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwFieldFlags,
    [in]  PCCOR_SIGNATURE pvSigBlob,
    [in]  ULONG       cbSigBlob,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue,
    [out] mdFieldDef  *pmd
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7de44-105">參數</span><span class="sxs-lookup"><span data-stu-id="7de44-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="7de44-106">在 `mdTypeDef` 封閉類別或介面的標記。</span><span class="sxs-lookup"><span data-stu-id="7de44-106">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="7de44-107">在Unicode 中的功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="7de44-107">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="7de44-108">在欄位屬性。</span><span class="sxs-lookup"><span data-stu-id="7de44-108">[in] The field attributes.</span></span> <span data-ttu-id="7de44-109">這是值的位元遮罩 `CorFieldAttr` 。</span><span class="sxs-lookup"><span data-stu-id="7de44-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="7de44-110">在作為 BLOB 的欄位簽名。</span><span class="sxs-lookup"><span data-stu-id="7de44-110">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="7de44-111">在中的位元組計數 `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="7de44-111">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="7de44-112">在`ELEMENT_TYPE_` *\** 常數值的。</span><span class="sxs-lookup"><span data-stu-id="7de44-112">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="7de44-113">這是一個 `CorElementType` 值。</span><span class="sxs-lookup"><span data-stu-id="7de44-113">This is a `CorElementType` value.</span></span> <span data-ttu-id="7de44-114">如果未定義欄位的常數值，請使用 `ELEMENT_TYPE_END` 。</span><span class="sxs-lookup"><span data-stu-id="7de44-114">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="7de44-115">在欄位的常數值。</span><span class="sxs-lookup"><span data-stu-id="7de44-115">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="7de44-116">在 (Unicode) 字元的大小 `pValue` 。</span><span class="sxs-lookup"><span data-stu-id="7de44-116">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="7de44-117">擴展 `mdFieldDef` 指派的權杖。</span><span class="sxs-lookup"><span data-stu-id="7de44-117">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7de44-118">需求</span><span class="sxs-lookup"><span data-stu-id="7de44-118">Requirements</span></span>  

 <span data-ttu-id="7de44-119">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7de44-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7de44-120">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="7de44-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7de44-121">連結 **庫：** 當做 MSCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="7de44-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7de44-122">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7de44-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7de44-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7de44-123">See also</span></span>

- [<span data-ttu-id="7de44-124">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="7de44-124">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="7de44-125">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="7de44-125">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
