---
title: IMetaDataImport::ResetEnum 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResetEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResetEnum
helpviewer_keywords:
- ResetEnum method [.NET Framework metadata]
- IMetaDataImport::ResetEnum method [.NET Framework metadata]
ms.assetid: dda867b5-1050-49ba-b01c-fcc83b7a5617
topic_type:
- apiref
ms.openlocfilehash: 52c35b3bd726d4c83c6745bf99940faa44ea7338
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702845"
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="a9fac-102">IMetaDataImport::ResetEnum 方法</span><span class="sxs-lookup"><span data-stu-id="a9fac-102">IMetaDataImport::ResetEnum Method</span></span>

<span data-ttu-id="a9fac-103">重設指定列舉程式至指定位置。</span><span class="sxs-lookup"><span data-stu-id="a9fac-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9fac-104">語法</span><span class="sxs-lookup"><span data-stu-id="a9fac-104">Syntax</span></span>  
  
```cpp  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,
   [in] ULONG       ulPos  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9fac-105">參數</span><span class="sxs-lookup"><span data-stu-id="a9fac-105">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="a9fac-106">在要重設的列舉值。</span><span class="sxs-lookup"><span data-stu-id="a9fac-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="a9fac-107">在要放置列舉值的新位置。</span><span class="sxs-lookup"><span data-stu-id="a9fac-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9fac-108">需求</span><span class="sxs-lookup"><span data-stu-id="a9fac-108">Requirements</span></span>  

 <span data-ttu-id="a9fac-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a9fac-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9fac-110">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="a9fac-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a9fac-111">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="a9fac-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a9fac-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9fac-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9fac-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9fac-113">See also</span></span>

- [<span data-ttu-id="a9fac-114">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="a9fac-114">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="a9fac-115">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="a9fac-115">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
