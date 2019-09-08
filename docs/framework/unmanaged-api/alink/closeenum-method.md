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
ms.openlocfilehash: 8d9529022eb04c81152dced5c63f255c510851a0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777468"
---
# <a name="closeenum-method"></a><span data-ttu-id="8e7be-102">CloseEnum 方法</span><span class="sxs-lookup"><span data-stu-id="8e7be-102">CloseEnum Method</span></span>
<span data-ttu-id="8e7be-103">關閉指示的列舉，並釋出相關聯的資源。</span><span class="sxs-lookup"><span data-stu-id="8e7be-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e7be-104">語法</span><span class="sxs-lookup"><span data-stu-id="8e7be-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e7be-105">參數</span><span class="sxs-lookup"><span data-stu-id="8e7be-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="8e7be-106">要關閉之列舉的控制碼。</span><span class="sxs-lookup"><span data-stu-id="8e7be-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e7be-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="8e7be-107">Return Value</span></span>  
 <span data-ttu-id="8e7be-108">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="8e7be-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e7be-109">需求</span><span class="sxs-lookup"><span data-stu-id="8e7be-109">Requirements</span></span>  
 <span data-ttu-id="8e7be-110">需要 alink. h</span><span class="sxs-lookup"><span data-stu-id="8e7be-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e7be-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e7be-111">See also</span></span>

- [<span data-ttu-id="8e7be-112">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="8e7be-112">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="8e7be-113">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="8e7be-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="8e7be-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="8e7be-114">ALink API</span></span>](index.md)
