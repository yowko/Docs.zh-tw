---
title: SetNonAssemblyFlags 方法
ms.date: 03/30/2017
api_name:
- IALink.SetNonAssemblyFlags
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetNonAssemblyFlags
helpviewer_keywords:
- SetNonAssemblyFlags method
ms.assetid: f8ba6fc8-f5aa-4066-ac96-56332758f5ec
topic_type:
- apiref
ms.openlocfilehash: b7bcf530947c161decc9c01c07df310550d69738
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733759"
---
# <a name="setnonassemblyflags-method"></a><span data-ttu-id="524dc-102">SetNonAssemblyFlags 方法</span><span class="sxs-lookup"><span data-stu-id="524dc-102">SetNonAssemblyFlags Method</span></span>

<span data-ttu-id="524dc-103">設定不是元件特有的旗標。</span><span class="sxs-lookup"><span data-stu-id="524dc-103">Sets flags that are not assembly-specific.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="524dc-104">語法</span><span class="sxs-lookup"><span data-stu-id="524dc-104">Syntax</span></span>  
  
```cpp  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="524dc-105">參數</span><span class="sxs-lookup"><span data-stu-id="524dc-105">Parameters</span></span>  

 `afFlags`  
 <span data-ttu-id="524dc-106">ALink 旗標。</span><span class="sxs-lookup"><span data-stu-id="524dc-106">ALink flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="524dc-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="524dc-107">Return Value</span></span>  

 <span data-ttu-id="524dc-108">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="524dc-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="524dc-109">需求</span><span class="sxs-lookup"><span data-stu-id="524dc-109">Requirements</span></span>  

 <span data-ttu-id="524dc-110">需要 alink。h</span><span class="sxs-lookup"><span data-stu-id="524dc-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="524dc-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="524dc-111">See also</span></span>

- [<span data-ttu-id="524dc-112">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="524dc-112">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="524dc-113">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="524dc-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="524dc-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="524dc-114">ALink API</span></span>](index.md)
