---
title: "IMetaDataImport::GetNameFromToken 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetNameFromToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetNameFromToken
helpviewer_keywords:
- GetNameFromToken method [.NET Framework metadata]
- IMetaDataImport::GetNameFromToken method [.NET Framework metadata]
ms.assetid: 32114ecf-8916-4ab2-a201-179c017344f1
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e77954d5730417a005c6c1ac07fa171bd0f1b13a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetnamefromtoken-method"></a><span data-ttu-id="a7a3b-102">IMetaDataImport::GetNameFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="a7a3b-102">IMetaDataImport::GetNameFromToken Method</span></span>
<span data-ttu-id="a7a3b-103">取得指定中繼資料語彙基元所參考物件的 UTF-8 名稱。</span><span class="sxs-lookup"><span data-stu-id="a7a3b-103">Gets the UTF-8 name of the object referenced by the specified metadata token.</span></span> <span data-ttu-id="a7a3b-104">這個方法已過時。</span><span class="sxs-lookup"><span data-stu-id="a7a3b-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7a3b-105">語法</span><span class="sxs-lookup"><span data-stu-id="a7a3b-105">Syntax</span></span>  
  
```  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a7a3b-106">參數</span><span class="sxs-lookup"><span data-stu-id="a7a3b-106">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="a7a3b-107">[in]語彙基元，代表要傳回的名稱的物件。</span><span class="sxs-lookup"><span data-stu-id="a7a3b-107">[in] The token representing the object to return the name for.</span></span>  
  
 `pszUtf8NamePtr`  
 <span data-ttu-id="a7a3b-108">[out]指向堆積中的 utf-8 物件名稱。</span><span class="sxs-lookup"><span data-stu-id="a7a3b-108">[out] A pointer to the UTF-8 object name in the heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7a3b-109">備註</span><span class="sxs-lookup"><span data-stu-id="a7a3b-109">Remarks</span></span>  
 <span data-ttu-id="a7a3b-110">`GetNameFromToken` 已經過時。</span><span class="sxs-lookup"><span data-stu-id="a7a3b-110">`GetNameFromToken` is obsolete.</span></span> <span data-ttu-id="a7a3b-111">或者，呼叫方法來取得特定的型別，例如所需的權杖的內容`GetFieldProps`欄位或`GetMethodProps`方法。</span><span class="sxs-lookup"><span data-stu-id="a7a3b-111">As an alternative, call a method to get the properties of the particular type of token required, such as `GetFieldProps` for a field or `GetMethodProps` for a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7a3b-112">需求</span><span class="sxs-lookup"><span data-stu-id="a7a3b-112">Requirements</span></span>  
 <span data-ttu-id="a7a3b-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a7a3b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7a3b-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a7a3b-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a7a3b-115">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a7a3b-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a7a3b-116">**.NET framework 版本：** 1.0</span><span class="sxs-lookup"><span data-stu-id="a7a3b-116">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7a3b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7a3b-117">See Also</span></span>  
 [<span data-ttu-id="a7a3b-118">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="a7a3b-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="a7a3b-119">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="a7a3b-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
