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
ms.openlocfilehash: a02456393680169ce33369ee5914f6c5216081c6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009213"
---
# <a name="imetadataemitsetmethodimplflags-method"></a><span data-ttu-id="1b691-102">IMetaDataEmit::SetMethodImplFlags 方法</span><span class="sxs-lookup"><span data-stu-id="1b691-102">IMetaDataEmit::SetMethodImplFlags Method</span></span>
<span data-ttu-id="1b691-103">設定或更新指定之標記所參考之繼承方法實的中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="1b691-103">Sets or updates the metadata signature of the inherited method implementation that is referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b691-104">語法</span><span class="sxs-lookup"><span data-stu-id="1b691-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodImplFlags (
    [in]  mdMethodDef   md,
    [in]  DWORD         dwImplFlags
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b691-105">參數</span><span class="sxs-lookup"><span data-stu-id="1b691-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="1b691-106">在要變更之方法的 token。</span><span class="sxs-lookup"><span data-stu-id="1b691-106">[in] The token for the method to be changed.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="1b691-107">在[CorMethodImpl](cormethodimpl-enumeration.md)列舉值的組合，可指定方法執行功能。</span><span class="sxs-lookup"><span data-stu-id="1b691-107">[in] A combination of the values of the [CorMethodImpl](cormethodimpl-enumeration.md) enumeration that specifies the method implementation features.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b691-108">需求</span><span class="sxs-lookup"><span data-stu-id="1b691-108">Requirements</span></span>  
 <span data-ttu-id="1b691-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1b691-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b691-110">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="1b691-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1b691-111">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="1b691-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b691-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b691-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b691-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b691-113">See also</span></span>

- [<span data-ttu-id="1b691-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="1b691-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="1b691-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="1b691-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
