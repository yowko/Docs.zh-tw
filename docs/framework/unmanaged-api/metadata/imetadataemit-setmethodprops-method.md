---
title: IMetaDataEmit::SetMethodProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodProps
helpviewer_keywords:
- SetMethodProps method [.NET Framework metadata]
- IMetaDataEmit::SetMethodProps method [.NET Framework metadata]
ms.assetid: e0c6ac12-22ea-43f5-b799-8cda0faf3336
topic_type:
- apiref
ms.openlocfilehash: c461582cc22f7185ee2707db91be83bc1aa0ba4c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706830"
---
# <a name="imetadataemitsetmethodprops-method"></a><span data-ttu-id="7b224-102">IMetaDataEmit::SetMethodProps 方法</span><span class="sxs-lookup"><span data-stu-id="7b224-102">IMetaDataEmit::SetMethodProps Method</span></span>

<span data-ttu-id="7b224-103">設定或更新由先前呼叫 [IMetaDataEmit：:D efinemethod](imetadataemit-definemethod-method.md)所定義方法的功能（儲存在指定的相對虛擬位址）。</span><span class="sxs-lookup"><span data-stu-id="7b224-103">Sets or updates the feature, stored at the specified relative virtual address, of a method defined by a prior call to [IMetaDataEmit::DefineMethod](imetadataemit-definemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b224-104">語法</span><span class="sxs-lookup"><span data-stu-id="7b224-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodProps (
    [in]  mdMethodDef md,
    [in]  DWORD       dwMethodFlags,  
    [in]  ULONG       ulCodeRVA,
    [in]  DWORD       dwImplFlags
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b224-105">參數</span><span class="sxs-lookup"><span data-stu-id="7b224-105">Parameters</span></span>  

 `md`  
 <span data-ttu-id="7b224-106">在要變更之方法的標記。</span><span class="sxs-lookup"><span data-stu-id="7b224-106">[in] The token for the method to be changed.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="7b224-107">在成員屬性。</span><span class="sxs-lookup"><span data-stu-id="7b224-107">[in] The member attributes.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="7b224-108">在程式碼的位址。</span><span class="sxs-lookup"><span data-stu-id="7b224-108">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="7b224-109">在方法的實旗標。</span><span class="sxs-lookup"><span data-stu-id="7b224-109">[in] The implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b224-110">需求</span><span class="sxs-lookup"><span data-stu-id="7b224-110">Requirements</span></span>  

 <span data-ttu-id="7b224-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7b224-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b224-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="7b224-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7b224-113">連結 **庫：** 當做 MSCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="7b224-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7b224-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b224-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b224-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b224-115">See also</span></span>

- [<span data-ttu-id="7b224-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="7b224-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="7b224-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="7b224-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
