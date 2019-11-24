---
title: IMetaDataImport::IsValidToken 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.IsValidToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::IsValidToken
helpviewer_keywords:
- IMetaDataImport::IsValidToken method [.NET Framework metadata]
- IsValidToken method [.NET Framework metadata]
ms.assetid: aeb0fc63-9eff-4384-9284-cb9900572d74
topic_type:
- apiref
ms.openlocfilehash: edf24de8ae38aab97e41a53cc86ae5aa6c592c50
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434698"
---
# <a name="imetadataimportisvalidtoken-method"></a><span data-ttu-id="941b3-102">IMetaDataImport::IsValidToken 方法</span><span class="sxs-lookup"><span data-stu-id="941b3-102">IMetaDataImport::IsValidToken Method</span></span>
<span data-ttu-id="941b3-103">取得一個值，用來表示指定語彙基元是否包含程式碼物件的有效參考。</span><span class="sxs-lookup"><span data-stu-id="941b3-103">Gets a value indicating whether the specified token holds a valid reference to a code object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="941b3-104">語法</span><span class="sxs-lookup"><span data-stu-id="941b3-104">Syntax</span></span>  
  
```cpp  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="941b3-105">參數</span><span class="sxs-lookup"><span data-stu-id="941b3-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="941b3-106">[in] The token to check the reference validity for.</span><span class="sxs-lookup"><span data-stu-id="941b3-106">[in] The token to check the reference validity for.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="941b3-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="941b3-107">Return Value</span></span>  
 <span data-ttu-id="941b3-108">`true` if `tk` is a valid metadata token within the current scope.</span><span class="sxs-lookup"><span data-stu-id="941b3-108">`true` if `tk` is a valid metadata token within the current scope.</span></span> <span data-ttu-id="941b3-109">否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="941b3-109">Otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="941b3-110">需求</span><span class="sxs-lookup"><span data-stu-id="941b3-110">Requirements</span></span>  
 <span data-ttu-id="941b3-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="941b3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="941b3-112">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="941b3-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="941b3-113">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="941b3-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="941b3-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="941b3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="941b3-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="941b3-115">See also</span></span>

- [<span data-ttu-id="941b3-116">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="941b3-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="941b3-117">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="941b3-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
