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
ms.openlocfilehash: 9b6c839cc664105149f26b0d21d7ba7fb91b3e29
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742208"
---
# <a name="closeenum-method"></a><span data-ttu-id="97115-102">CloseEnum 方法</span><span class="sxs-lookup"><span data-stu-id="97115-102">CloseEnum Method</span></span>
<span data-ttu-id="97115-103">關閉指定的列舉型別，並釋放相關聯的資源。</span><span class="sxs-lookup"><span data-stu-id="97115-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97115-104">語法</span><span class="sxs-lookup"><span data-stu-id="97115-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="97115-105">參數</span><span class="sxs-lookup"><span data-stu-id="97115-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="97115-106">若要關閉的列舉型別的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="97115-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97115-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="97115-107">Return Value</span></span>  
 <span data-ttu-id="97115-108">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="97115-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97115-109">需求</span><span class="sxs-lookup"><span data-stu-id="97115-109">Requirements</span></span>  
 <span data-ttu-id="97115-110">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="97115-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97115-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97115-111">See also</span></span>

- [<span data-ttu-id="97115-112">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="97115-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="97115-113">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="97115-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="97115-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="97115-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
