---
title: IMetaDataEmit::GetTokenFromTypeSpec 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetTokenFromTypeSpec
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetTokenFromTypeSpec
helpviewer_keywords:
- GetTokenFromTypeSpec method [.NET Framework metadata]
- IMetaDataEmit::GetTokenFromTypeSpec method [.NET Framework metadata]
ms.assetid: 7de6447a-a751-49d8-87e2-951cee77b536
topic_type:
- apiref
ms.openlocfilehash: 3a8f369728b8464850259518981bf6690cb17a01
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722033"
---
# <a name="imetadataemitgettokenfromtypespec-method"></a><span data-ttu-id="f750a-102">IMetaDataEmit::GetTokenFromTypeSpec 方法</span><span class="sxs-lookup"><span data-stu-id="f750a-102">IMetaDataEmit::GetTokenFromTypeSpec Method</span></span>

<span data-ttu-id="f750a-103">取得具有指定中繼資料簽章之類型的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="f750a-103">Gets a metadata token for the type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f750a-104">語法</span><span class="sxs-lookup"><span data-stu-id="f750a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromTypeSpec (
    [in]  PCCOR_SIGNATURE       pvSig,
    [in]  ULONG                 cbSig,
    [out] mdTypeSpec            *ptypespec
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f750a-105">參數</span><span class="sxs-lookup"><span data-stu-id="f750a-105">Parameters</span></span>  

 `pvSig`  
 <span data-ttu-id="f750a-106">在要定義的簽章。</span><span class="sxs-lookup"><span data-stu-id="f750a-106">[in] The signature being defined.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="f750a-107">在中的位元組計數 `pvSig` 。</span><span class="sxs-lookup"><span data-stu-id="f750a-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `ptypespec`  
 <span data-ttu-id="f750a-108">擴展 `mdTypeSpec` 指派的權杖。</span><span class="sxs-lookup"><span data-stu-id="f750a-108">[out] The `mdTypeSpec` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f750a-109">需求</span><span class="sxs-lookup"><span data-stu-id="f750a-109">Requirements</span></span>  

 <span data-ttu-id="f750a-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f750a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f750a-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="f750a-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f750a-112">連結 **庫：** 當做 MSCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="f750a-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f750a-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f750a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f750a-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f750a-114">See also</span></span>

- [<span data-ttu-id="f750a-115">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="f750a-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="f750a-116">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="f750a-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
