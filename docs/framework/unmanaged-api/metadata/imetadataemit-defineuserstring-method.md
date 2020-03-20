---
title: IMetaDataEmit::DefineUserString 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineUserString
helpviewer_keywords:
- DefineUserString method [.NET Framework metadata]
- IMetaDataEmit::DefineUserString method [.NET Framework metadata]
ms.assetid: 88fb7ef3-bbdf-429c-b678-c9c153456461
topic_type:
- apiref
ms.openlocfilehash: a71d8694ec8c5bd35ecd3e98ed32e05bc7b382fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177624"
---
# <a name="imetadataemitdefineuserstring-method"></a><span data-ttu-id="8bca4-102">IMetaDataEmit::DefineUserString 方法</span><span class="sxs-lookup"><span data-stu-id="8bca4-102">IMetaDataEmit::DefineUserString Method</span></span>
<span data-ttu-id="8bca4-103">獲取指定文本字串的中繼資料權杖。</span><span class="sxs-lookup"><span data-stu-id="8bca4-103">Gets a metadata token for the specified literal string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bca4-104">語法</span><span class="sxs-lookup"><span data-stu-id="8bca4-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineUserString (
    [in]  LPCWSTR     szString,
    [in]  ULONG       cchString,
    [out] mdString    *pstk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8bca4-105">參數</span><span class="sxs-lookup"><span data-stu-id="8bca4-105">Parameters</span></span>  
 `szString`  
 <span data-ttu-id="8bca4-106">[在]要存儲的使用者字串。</span><span class="sxs-lookup"><span data-stu-id="8bca4-106">[in] The user string to store.</span></span>  
  
 `cchString`  
 <span data-ttu-id="8bca4-107">[在]中的`szString`寬字元的計數。</span><span class="sxs-lookup"><span data-stu-id="8bca4-107">[in] The count of wide characters in `szString`.</span></span>  
  
 `pstk`  
 <span data-ttu-id="8bca4-108">[出]分配的字串權杖。</span><span class="sxs-lookup"><span data-stu-id="8bca4-108">[out] The string token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bca4-109">需求</span><span class="sxs-lookup"><span data-stu-id="8bca4-109">Requirements</span></span>  
 <span data-ttu-id="8bca4-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8bca4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bca4-111">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="8bca4-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8bca4-112">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8bca4-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8bca4-113">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bca4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bca4-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8bca4-114">See also</span></span>

- [<span data-ttu-id="8bca4-115">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="8bca4-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="8bca4-116">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="8bca4-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
