---
title: IMetaDataEmit::SetParent 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParent
helpviewer_keywords:
- SetParent method [.NET Framework metadata]
- IMetaDataEmit::SetParent method [.NET Framework metadata]
ms.assetid: 02a02ff7-ae0e-4692-a20e-372405f23052
topic_type:
- apiref
ms.openlocfilehash: d821413e67b36392d936499cd22f2e065f1556ec
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503844"
---
# <a name="imetadataemitsetparent-method"></a><span data-ttu-id="4696b-102">IMetaDataEmit::SetParent 方法</span><span class="sxs-lookup"><span data-stu-id="4696b-102">IMetaDataEmit::SetParent Method</span></span>
<span data-ttu-id="4696b-103">建立指定的成員（如先前呼叫[IMetaDataEmit：:D efinememberref](imetadataemit-definememberref-method.md)所定義）是指定類型的成員，如先前的[IMetaDataEmit：:D efinetypedef](imetadataemit-definetypedef-method.md)呼叫所定義。</span><span class="sxs-lookup"><span data-stu-id="4696b-103">Establishes that the specified member, as defined by a prior call to [IMetaDataEmit::DefineMemberRef](imetadataemit-definememberref-method.md), is a member of the specified type, as defined by a prior call to [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4696b-104">語法</span><span class="sxs-lookup"><span data-stu-id="4696b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetParent (
    [in]  mdMemberRef mr,
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4696b-105">參數</span><span class="sxs-lookup"><span data-stu-id="4696b-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="4696b-106">在`mdMemberRef`要接收新父系的 token。</span><span class="sxs-lookup"><span data-stu-id="4696b-106">[in] The `mdMemberRef` token to receive a new parent.</span></span>  
  
 `tk`  
 <span data-ttu-id="4696b-107">在`mdToken`新父系的。</span><span class="sxs-lookup"><span data-stu-id="4696b-107">[in] The `mdToken` for the new parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4696b-108">規格需求</span><span class="sxs-lookup"><span data-stu-id="4696b-108">Requirements</span></span>  
 <span data-ttu-id="4696b-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4696b-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4696b-110">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="4696b-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4696b-111">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="4696b-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4696b-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4696b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4696b-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4696b-113">See also</span></span>

- [<span data-ttu-id="4696b-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="4696b-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="4696b-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="4696b-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
