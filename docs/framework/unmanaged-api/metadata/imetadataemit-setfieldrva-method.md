---
title: IMetaDataEmit::SetFieldRVA 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldRVA
helpviewer_keywords:
- IMetaDataEmit::SetFieldRVA method [.NET Framework metadata]
- SetFieldRVA method [.NET Framework metadata]
ms.assetid: 6dc37f9d-87ee-4cb3-9216-ced600184ce8
topic_type:
- apiref
ms.openlocfilehash: d429995e41006798aee5f796150bedbd6ae87f6f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003863"
---
# <a name="imetadataemitsetfieldrva-method"></a><span data-ttu-id="57164-102">IMetaDataEmit::SetFieldRVA 方法</span><span class="sxs-lookup"><span data-stu-id="57164-102">IMetaDataEmit::SetFieldRVA Method</span></span>
<span data-ttu-id="57164-103">針對指定之標記所參考的欄位，設定其相對虛擬位址的全域變數值。</span><span class="sxs-lookup"><span data-stu-id="57164-103">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57164-104">語法</span><span class="sxs-lookup"><span data-stu-id="57164-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldRVA (
    [in]  mdFieldDef  fd,
    [in]  ULONG       ulRVA
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57164-105">參數</span><span class="sxs-lookup"><span data-stu-id="57164-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="57164-106">在目標欄位的 token。</span><span class="sxs-lookup"><span data-stu-id="57164-106">[in] The token for the target field.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="57164-107">在程式碼或資料區域的位址。</span><span class="sxs-lookup"><span data-stu-id="57164-107">[in] The address of a code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57164-108">需求</span><span class="sxs-lookup"><span data-stu-id="57164-108">Requirements</span></span>  
 <span data-ttu-id="57164-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="57164-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57164-110">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="57164-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="57164-111">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="57164-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57164-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57164-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57164-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57164-113">See also</span></span>

- [<span data-ttu-id="57164-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="57164-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="57164-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="57164-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
