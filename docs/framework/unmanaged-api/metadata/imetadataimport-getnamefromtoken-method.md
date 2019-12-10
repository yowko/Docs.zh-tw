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
ms.openlocfilehash: 6ed30f07fcec9c730e1514350c594399f0aa16e5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437270"
---
# <a name="imetadataimportgetnamefromtoken-method"></a><span data-ttu-id="31f7f-102">IMetaDataImport::GetNameFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="31f7f-102">IMetaDataImport::GetNameFromToken Method</span></span>
<span data-ttu-id="31f7f-103">取得指定中繼資料語彙基元所參考物件的 UTF-8 名稱。</span><span class="sxs-lookup"><span data-stu-id="31f7f-103">Gets the UTF-8 name of the object referenced by the specified metadata token.</span></span> <span data-ttu-id="31f7f-104">這個方法已過時。</span><span class="sxs-lookup"><span data-stu-id="31f7f-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31f7f-105">語法</span><span class="sxs-lookup"><span data-stu-id="31f7f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31f7f-106">參數</span><span class="sxs-lookup"><span data-stu-id="31f7f-106">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="31f7f-107">在Token，代表要傳回名稱的物件。</span><span class="sxs-lookup"><span data-stu-id="31f7f-107">[in] The token representing the object to return the name for.</span></span>  
  
 `pszUtf8NamePtr`  
 <span data-ttu-id="31f7f-108">脫銷堆積中 UTF-8 物件名稱的指標。</span><span class="sxs-lookup"><span data-stu-id="31f7f-108">[out] A pointer to the UTF-8 object name in the heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31f7f-109">備註</span><span class="sxs-lookup"><span data-stu-id="31f7f-109">Remarks</span></span>  
 <span data-ttu-id="31f7f-110">`GetNameFromToken` 已經過時。</span><span class="sxs-lookup"><span data-stu-id="31f7f-110">`GetNameFromToken` is obsolete.</span></span> <span data-ttu-id="31f7f-111">或者，呼叫方法來取得所需之特定權杖類型的屬性，例如欄位的 `GetFieldProps`，或方法的 `GetMethodProps`。</span><span class="sxs-lookup"><span data-stu-id="31f7f-111">As an alternative, call a method to get the properties of the particular type of token required, such as `GetFieldProps` for a field or `GetMethodProps` for a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31f7f-112">需求</span><span class="sxs-lookup"><span data-stu-id="31f7f-112">Requirements</span></span>  
 <span data-ttu-id="31f7f-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="31f7f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31f7f-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="31f7f-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="31f7f-115">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="31f7f-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="31f7f-116">**.NET Framework 版本：** 1.0</span><span class="sxs-lookup"><span data-stu-id="31f7f-116">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31f7f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31f7f-117">See also</span></span>

- [<span data-ttu-id="31f7f-118">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="31f7f-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="31f7f-119">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="31f7f-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
