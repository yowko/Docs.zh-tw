---
title: IMetaDataImport::GetUserString 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetUserString
helpviewer_keywords:
- IMetaDataImport::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 0fd3bb47-58b5-4083-b241-b9719df7a285
topic_type:
- apiref
ms.openlocfilehash: 358ca84f32e1b233116605bf5486cc9a01b42e67
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503495"
---
# <a name="imetadataimportgetuserstring-method"></a><span data-ttu-id="d1370-102">IMetaDataImport::GetUserString 方法</span><span class="sxs-lookup"><span data-stu-id="d1370-102">IMetaDataImport::GetUserString Method</span></span>
<span data-ttu-id="d1370-103">取得指定中繼資料語彙基元所代表的常值字串。</span><span class="sxs-lookup"><span data-stu-id="d1370-103">Gets the literal string represented by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1370-104">語法</span><span class="sxs-lookup"><span data-stu-id="d1370-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserString (  
   [in]   mdString    stk,  
   [out]  LPWSTR      szString,  
   [in]   ULONG       cchString,  
   [out]  ULONG       *pchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1370-105">參數</span><span class="sxs-lookup"><span data-stu-id="d1370-105">Parameters</span></span>  
 `stk`  
 <span data-ttu-id="d1370-106">在要為其傳回相關聯字串的字串標記。</span><span class="sxs-lookup"><span data-stu-id="d1370-106">[in] The String token to return the associated string for.</span></span>  
  
 `szString`  
 <span data-ttu-id="d1370-107">脫銷要求之字串的複本。</span><span class="sxs-lookup"><span data-stu-id="d1370-107">[out] A copy of the requested string.</span></span>  
  
 `cchString`  
 <span data-ttu-id="d1370-108">在所要求的大小上限，以寬字元為單位 `szString` 。</span><span class="sxs-lookup"><span data-stu-id="d1370-108">[in] The maximum size in wide characters of the requested `szString`.</span></span>  
  
 `pchString`  
 <span data-ttu-id="d1370-109">脫銷傳回之的大小（以寬字元為單位） `szString` 。</span><span class="sxs-lookup"><span data-stu-id="d1370-109">[out] The size in wide characters of the returned `szString`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1370-110">規格需求</span><span class="sxs-lookup"><span data-stu-id="d1370-110">Requirements</span></span>  
 <span data-ttu-id="d1370-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d1370-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1370-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="d1370-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d1370-113">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d1370-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d1370-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1370-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1370-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1370-115">See also</span></span>

- [<span data-ttu-id="d1370-116">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="d1370-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="d1370-117">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="d1370-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
