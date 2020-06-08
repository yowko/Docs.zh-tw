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
ms.openlocfilehash: bc7f1740d666211b63cd93e6f1c0e6955f61ec5d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503454"
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="ed979-102">IMetaDataImport::ResetEnum 方法</span><span class="sxs-lookup"><span data-stu-id="ed979-102">IMetaDataImport::ResetEnum Method</span></span>
<span data-ttu-id="ed979-103">重設指定列舉程式至指定位置。</span><span class="sxs-lookup"><span data-stu-id="ed979-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed979-104">語法</span><span class="sxs-lookup"><span data-stu-id="ed979-104">Syntax</span></span>  
  
```cpp  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,
   [in] ULONG       ulPos  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed979-105">參數</span><span class="sxs-lookup"><span data-stu-id="ed979-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="ed979-106">在要重設的列舉值。</span><span class="sxs-lookup"><span data-stu-id="ed979-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="ed979-107">在要放置枚舉器的新位置。</span><span class="sxs-lookup"><span data-stu-id="ed979-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed979-108">規格需求</span><span class="sxs-lookup"><span data-stu-id="ed979-108">Requirements</span></span>  
 <span data-ttu-id="ed979-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ed979-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed979-110">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="ed979-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ed979-111">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ed979-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ed979-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed979-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed979-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed979-113">See also</span></span>

- [<span data-ttu-id="ed979-114">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="ed979-114">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="ed979-115">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="ed979-115">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
