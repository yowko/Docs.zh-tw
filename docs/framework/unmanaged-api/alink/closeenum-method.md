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
ms.openlocfilehash: 59b1ec3f9ca382ef13680e3aad4d0c0c0e175f1c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716963"
---
# <a name="closeenum-method"></a><span data-ttu-id="5c520-102">CloseEnum 方法</span><span class="sxs-lookup"><span data-stu-id="5c520-102">CloseEnum Method</span></span>

<span data-ttu-id="5c520-103">關閉指出的列舉並釋出相關聯的資源。</span><span class="sxs-lookup"><span data-stu-id="5c520-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c520-104">語法</span><span class="sxs-lookup"><span data-stu-id="5c520-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c520-105">參數</span><span class="sxs-lookup"><span data-stu-id="5c520-105">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="5c520-106">要關閉之列舉的控制碼。</span><span class="sxs-lookup"><span data-stu-id="5c520-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c520-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="5c520-107">Return Value</span></span>  

 <span data-ttu-id="5c520-108">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="5c520-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c520-109">需求</span><span class="sxs-lookup"><span data-stu-id="5c520-109">Requirements</span></span>  

 <span data-ttu-id="5c520-110">需要 alink。h</span><span class="sxs-lookup"><span data-stu-id="5c520-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c520-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c520-111">See also</span></span>

- [<span data-ttu-id="5c520-112">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="5c520-112">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="5c520-113">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="5c520-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="5c520-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="5c520-114">ALink API</span></span>](index.md)
