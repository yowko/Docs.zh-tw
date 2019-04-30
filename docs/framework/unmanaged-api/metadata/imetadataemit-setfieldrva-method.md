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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4ebde1d506a120a99e1c637c660b45d698994f5a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992468"
---
# <a name="imetadataemitsetfieldrva-method"></a><span data-ttu-id="0eb14-102">IMetaDataEmit::SetFieldRVA 方法</span><span class="sxs-lookup"><span data-stu-id="0eb14-102">IMetaDataEmit::SetFieldRVA Method</span></span>
<span data-ttu-id="0eb14-103">設定全域變數的值，指定語彙基元所參考之欄位的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="0eb14-103">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0eb14-104">語法</span><span class="sxs-lookup"><span data-stu-id="0eb14-104">Syntax</span></span>  
  
```  
HRESULT SetFieldRVA (   
    [in]  mdFieldDef  fd,   
    [in]  ULONG       ulRVA   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0eb14-105">參數</span><span class="sxs-lookup"><span data-stu-id="0eb14-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="0eb14-106">[in]目標欄位的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="0eb14-106">[in] The token for the target field.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="0eb14-107">[in]程式碼或資料區域的位址。</span><span class="sxs-lookup"><span data-stu-id="0eb14-107">[in] The address of a code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0eb14-108">需求</span><span class="sxs-lookup"><span data-stu-id="0eb14-108">Requirements</span></span>  
 <span data-ttu-id="0eb14-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0eb14-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0eb14-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0eb14-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0eb14-111">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0eb14-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0eb14-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0eb14-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0eb14-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0eb14-113">See also</span></span>

- [<span data-ttu-id="0eb14-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="0eb14-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="0eb14-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="0eb14-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
