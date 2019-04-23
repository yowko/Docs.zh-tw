---
title: Init 方法
ms.date: 03/30/2017
api_name:
- IALink.Init
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- Init
helpviewer_keywords:
- Init method
ms.assetid: e48b5c64-049f-4f93-ad87-d07ae9cd5845
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 60602462376543fe934bb3c58bc4988fa8ab34bf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119362"
---
# <a name="init-method"></a><span data-ttu-id="ba055-102">Init 方法</span><span class="sxs-lookup"><span data-stu-id="ba055-102">Init Method</span></span>
<span data-ttu-id="ba055-103">準備實作的物件[IALink 介面](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)供使用。</span><span class="sxs-lookup"><span data-stu-id="ba055-103">Prepares objects implementing the [IALink Interface](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md) for use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba055-104">語法</span><span class="sxs-lookup"><span data-stu-id="ba055-104">Syntax</span></span>  
  
```  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba055-105">參數</span><span class="sxs-lookup"><span data-stu-id="ba055-105">Parameters</span></span>  
 `pDispenser`  
 <span data-ttu-id="ba055-106">[IMetaDataDispenserEx 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)指標的中繼資料的分配程式。</span><span class="sxs-lookup"><span data-stu-id="ba055-106">[IMetaDataDispenserEx Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md) pointer to the metadata dispenser.</span></span>  
  
 `pErrorHandler`  
 <span data-ttu-id="ba055-107">[IMetaDataError 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)選擇性錯誤處理介面指標。</span><span class="sxs-lookup"><span data-stu-id="ba055-107">[IMetaDataError Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) pointer to an optional error handling interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ba055-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="ba055-108">Return Value</span></span>  
 <span data-ttu-id="ba055-109">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="ba055-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba055-110">需求</span><span class="sxs-lookup"><span data-stu-id="ba055-110">Requirements</span></span>  
 <span data-ttu-id="ba055-111">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="ba055-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba055-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba055-112">See also</span></span>

- [<span data-ttu-id="ba055-113">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="ba055-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="ba055-114">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="ba055-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="ba055-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="ba055-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
