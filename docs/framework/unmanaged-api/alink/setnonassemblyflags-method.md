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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e8a22e958740b69ba0e09bf062bf4d86075c3ff1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777018"
---
# <a name="setnonassemblyflags-method"></a><span data-ttu-id="35ed2-102">SetNonAssemblyFlags 方法</span><span class="sxs-lookup"><span data-stu-id="35ed2-102">SetNonAssemblyFlags Method</span></span>
<span data-ttu-id="35ed2-103">設定不是元件特有的旗標。</span><span class="sxs-lookup"><span data-stu-id="35ed2-103">Sets flags that are not assembly-specific.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35ed2-104">語法</span><span class="sxs-lookup"><span data-stu-id="35ed2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="35ed2-105">參數</span><span class="sxs-lookup"><span data-stu-id="35ed2-105">Parameters</span></span>  
 `afFlags`  
 <span data-ttu-id="35ed2-106">ALink 旗標。</span><span class="sxs-lookup"><span data-stu-id="35ed2-106">ALink flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="35ed2-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="35ed2-107">Return Value</span></span>  
 <span data-ttu-id="35ed2-108">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="35ed2-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35ed2-109">需求</span><span class="sxs-lookup"><span data-stu-id="35ed2-109">Requirements</span></span>  
 <span data-ttu-id="35ed2-110">需要 alink. h</span><span class="sxs-lookup"><span data-stu-id="35ed2-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35ed2-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35ed2-111">See also</span></span>

- [<span data-ttu-id="35ed2-112">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="35ed2-112">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="35ed2-113">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="35ed2-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="35ed2-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="35ed2-114">ALink API</span></span>](index.md)
