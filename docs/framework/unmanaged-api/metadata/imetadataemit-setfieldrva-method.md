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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59181671"
---
# <a name="imetadataemitsetfieldrva-method"></a><span data-ttu-id="c1969-102">IMetaDataEmit::SetFieldRVA 方法</span><span class="sxs-lookup"><span data-stu-id="c1969-102">IMetaDataEmit::SetFieldRVA Method</span></span>
<span data-ttu-id="c1969-103">設定全域變數的值，指定語彙基元所參考之欄位的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="c1969-103">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1969-104">語法</span><span class="sxs-lookup"><span data-stu-id="c1969-104">Syntax</span></span>  
  
```  
HRESULT SetFieldRVA (   
    [in]  mdFieldDef  fd,   
    [in]  ULONG       ulRVA   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1969-105">參數</span><span class="sxs-lookup"><span data-stu-id="c1969-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="c1969-106">[in]目標欄位的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="c1969-106">[in] The token for the target field.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="c1969-107">[in]程式碼或資料區域的位址。</span><span class="sxs-lookup"><span data-stu-id="c1969-107">[in] The address of a code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1969-108">需求</span><span class="sxs-lookup"><span data-stu-id="c1969-108">Requirements</span></span>  
 <span data-ttu-id="c1969-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c1969-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1969-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c1969-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c1969-111">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c1969-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="c1969-112">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="c1969-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c1969-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1969-113">See also</span></span>

- [<span data-ttu-id="c1969-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="c1969-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="c1969-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="c1969-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
