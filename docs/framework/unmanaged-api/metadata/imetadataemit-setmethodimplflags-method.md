---
title: IMetaDataEmit::SetMethodImplFlags 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodImplFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodImplFlags
helpviewer_keywords:
- IMetaDataEmit::SetMethodImplFlags method [.NET Framework metadata]
- SetMethodImpFlags method [.NET Framework metadata]
ms.assetid: 4bc82d9b-9544-4be3-ba51-a2d4d806158a
topic_type:
- apiref
ms.openlocfilehash: 486d545413337f6696bd9f21c516466fc3747256
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730353"
---
# <a name="imetadataemitsetmethodimplflags-method"></a><span data-ttu-id="33e76-102">IMetaDataEmit::SetMethodImplFlags 方法</span><span class="sxs-lookup"><span data-stu-id="33e76-102">IMetaDataEmit::SetMethodImplFlags Method</span></span>

<span data-ttu-id="33e76-103">設定或更新所指定標記所參考之繼承方法執行的中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="33e76-103">Sets or updates the metadata signature of the inherited method implementation that is referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33e76-104">語法</span><span class="sxs-lookup"><span data-stu-id="33e76-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodImplFlags (
    [in]  mdMethodDef   md,
    [in]  DWORD         dwImplFlags
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33e76-105">參數</span><span class="sxs-lookup"><span data-stu-id="33e76-105">Parameters</span></span>  

 `md`  
 <span data-ttu-id="33e76-106">在要變更之方法的標記。</span><span class="sxs-lookup"><span data-stu-id="33e76-106">[in] The token for the method to be changed.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="33e76-107">在 [CorMethodImpl](cormethodimpl-enumeration.md) 列舉值的組合，指定方法執行功能。</span><span class="sxs-lookup"><span data-stu-id="33e76-107">[in] A combination of the values of the [CorMethodImpl](cormethodimpl-enumeration.md) enumeration that specifies the method implementation features.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33e76-108">需求</span><span class="sxs-lookup"><span data-stu-id="33e76-108">Requirements</span></span>  

 <span data-ttu-id="33e76-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="33e76-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33e76-110">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="33e76-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="33e76-111">連結 **庫：** 當做 MSCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="33e76-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="33e76-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33e76-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33e76-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33e76-113">See also</span></span>

- [<span data-ttu-id="33e76-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="33e76-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="33e76-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="33e76-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
