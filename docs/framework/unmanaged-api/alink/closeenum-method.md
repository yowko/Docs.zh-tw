---
title: CloseEnum 方法
ms.date: 03/30/2017
api_name:
- CloseEnum
- IALink.CloseEnum
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseEnum
helpviewer_keywords:
- CloseEnum method
ms.assetid: aa4a091e-13fe-4264-91de-e12f1c767c87
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e5c3185dc6d488223d5882f543f0c690d82261b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402440"
---
# <a name="closeenum-method"></a><span data-ttu-id="81fa0-102">CloseEnum 方法</span><span class="sxs-lookup"><span data-stu-id="81fa0-102">CloseEnum Method</span></span>
<span data-ttu-id="81fa0-103">關閉指定的列舉型別，並釋放相關聯的資源。</span><span class="sxs-lookup"><span data-stu-id="81fa0-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81fa0-104">語法</span><span class="sxs-lookup"><span data-stu-id="81fa0-104">Syntax</span></span>  
  
```  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="81fa0-105">參數</span><span class="sxs-lookup"><span data-stu-id="81fa0-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="81fa0-106">要關閉的列舉控制代碼。</span><span class="sxs-lookup"><span data-stu-id="81fa0-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81fa0-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="81fa0-107">Return Value</span></span>  
 <span data-ttu-id="81fa0-108">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="81fa0-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81fa0-109">需求</span><span class="sxs-lookup"><span data-stu-id="81fa0-109">Requirements</span></span>  
 <span data-ttu-id="81fa0-110">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="81fa0-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81fa0-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81fa0-111">See Also</span></span>  
 [<span data-ttu-id="81fa0-112">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="81fa0-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="81fa0-113">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="81fa0-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="81fa0-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="81fa0-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
