---
title: IMetaDataImport::GetNameFromToken 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNameFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNameFromToken
helpviewer_keywords:
- GetNameFromToken method [.NET Framework metadata]
- IMetaDataImport::GetNameFromToken method [.NET Framework metadata]
ms.assetid: 32114ecf-8916-4ab2-a201-179c017344f1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d77891478c9136a18dc4c9c44beed805244dd1a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225933"
---
# <a name="imetadataimportgetnamefromtoken-method"></a><span data-ttu-id="51012-102">IMetaDataImport::GetNameFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="51012-102">IMetaDataImport::GetNameFromToken Method</span></span>
<span data-ttu-id="51012-103">取得指定中繼資料語彙基元所參考物件的 UTF-8 名稱。</span><span class="sxs-lookup"><span data-stu-id="51012-103">Gets the UTF-8 name of the object referenced by the specified metadata token.</span></span> <span data-ttu-id="51012-104">這個方法已過時。</span><span class="sxs-lookup"><span data-stu-id="51012-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51012-105">語法</span><span class="sxs-lookup"><span data-stu-id="51012-105">Syntax</span></span>  
  
```  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51012-106">參數</span><span class="sxs-lookup"><span data-stu-id="51012-106">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="51012-107">[in]語彙基元，表示要傳回的名稱的物件。</span><span class="sxs-lookup"><span data-stu-id="51012-107">[in] The token representing the object to return the name for.</span></span>  
  
 `pszUtf8NamePtr`  
 <span data-ttu-id="51012-108">[out]指向的堆積中的 utf-8 物件名稱。</span><span class="sxs-lookup"><span data-stu-id="51012-108">[out] A pointer to the UTF-8 object name in the heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51012-109">備註</span><span class="sxs-lookup"><span data-stu-id="51012-109">Remarks</span></span>  
 <span data-ttu-id="51012-110">`GetNameFromToken` 已經過時。</span><span class="sxs-lookup"><span data-stu-id="51012-110">`GetNameFromToken` is obsolete.</span></span> <span data-ttu-id="51012-111">或者，呼叫方法來取得必要的這類的語彙基元的特定類型的屬性`GetFieldProps`欄位或`GetMethodProps`方法。</span><span class="sxs-lookup"><span data-stu-id="51012-111">As an alternative, call a method to get the properties of the particular type of token required, such as `GetFieldProps` for a field or `GetMethodProps` for a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51012-112">需求</span><span class="sxs-lookup"><span data-stu-id="51012-112">Requirements</span></span>  
 <span data-ttu-id="51012-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="51012-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51012-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="51012-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="51012-115">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="51012-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="51012-116">**.NET framework 版本：** 1.0</span><span class="sxs-lookup"><span data-stu-id="51012-116">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51012-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51012-117">See also</span></span>

- [<span data-ttu-id="51012-118">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="51012-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="51012-119">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="51012-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
