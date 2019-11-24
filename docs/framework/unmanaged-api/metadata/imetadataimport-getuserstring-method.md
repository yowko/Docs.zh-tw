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
ms.openlocfilehash: 690abec6104f6eed1ad5a0eae9a6b6bb18d35b0d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436682"
---
# <a name="imetadataimportgetuserstring-method"></a><span data-ttu-id="71038-102">IMetaDataImport::GetUserString 方法</span><span class="sxs-lookup"><span data-stu-id="71038-102">IMetaDataImport::GetUserString Method</span></span>
<span data-ttu-id="71038-103">取得指定中繼資料語彙基元所代表的常值字串。</span><span class="sxs-lookup"><span data-stu-id="71038-103">Gets the literal string represented by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71038-104">語法</span><span class="sxs-lookup"><span data-stu-id="71038-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserString (  
   [in]   mdString    stk,  
   [out]  LPWSTR      szString,  
   [in]   ULONG       cchString,  
   [out]  ULONG       *pchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71038-105">參數</span><span class="sxs-lookup"><span data-stu-id="71038-105">Parameters</span></span>  
 `stk`  
 <span data-ttu-id="71038-106">[in] The String token to return the associated string for.</span><span class="sxs-lookup"><span data-stu-id="71038-106">[in] The String token to return the associated string for.</span></span>  
  
 `szString`  
 <span data-ttu-id="71038-107">[out] A copy of the requested string.</span><span class="sxs-lookup"><span data-stu-id="71038-107">[out] A copy of the requested string.</span></span>  
  
 `cchString`  
 <span data-ttu-id="71038-108">[in] The maximum size in wide characters of the requested `szString`.</span><span class="sxs-lookup"><span data-stu-id="71038-108">[in] The maximum size in wide characters of the requested `szString`.</span></span>  
  
 `pchString`  
 <span data-ttu-id="71038-109">[out] The size in wide characters of the returned `szString`.</span><span class="sxs-lookup"><span data-stu-id="71038-109">[out] The size in wide characters of the returned `szString`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71038-110">需求</span><span class="sxs-lookup"><span data-stu-id="71038-110">Requirements</span></span>  
 <span data-ttu-id="71038-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="71038-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71038-112">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="71038-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="71038-113">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="71038-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="71038-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71038-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71038-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="71038-115">See also</span></span>

- [<span data-ttu-id="71038-116">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="71038-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="71038-117">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="71038-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
