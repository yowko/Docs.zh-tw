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
ms.openlocfilehash: 3f965ab215ff861c6df61de82dcbbea6b389c8da
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426775"
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="b7019-102">IMetaDataImport::ResetEnum 方法</span><span class="sxs-lookup"><span data-stu-id="b7019-102">IMetaDataImport::ResetEnum Method</span></span>
<span data-ttu-id="b7019-103">重設指定列舉程式至指定位置。</span><span class="sxs-lookup"><span data-stu-id="b7019-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7019-104">語法</span><span class="sxs-lookup"><span data-stu-id="b7019-104">Syntax</span></span>  
  
```cpp  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,   
   [in] ULONG       ulPos  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7019-105">參數</span><span class="sxs-lookup"><span data-stu-id="b7019-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="b7019-106">在要重設的列舉值。</span><span class="sxs-lookup"><span data-stu-id="b7019-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="b7019-107">在要放置枚舉器的新位置。</span><span class="sxs-lookup"><span data-stu-id="b7019-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7019-108">需求</span><span class="sxs-lookup"><span data-stu-id="b7019-108">Requirements</span></span>  
 <span data-ttu-id="b7019-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b7019-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7019-110">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="b7019-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b7019-111">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b7019-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b7019-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7019-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7019-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="b7019-113">See also</span></span>

- [<span data-ttu-id="b7019-114">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="b7019-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b7019-115">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="b7019-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
