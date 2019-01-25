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
ms.openlocfilehash: 78a7dab69e716e1662a277a69c008474d97f9bc4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619645"
---
# <a name="setnonassemblyflags-method"></a><span data-ttu-id="93738-102">SetNonAssemblyFlags 方法</span><span class="sxs-lookup"><span data-stu-id="93738-102">SetNonAssemblyFlags Method</span></span>
<span data-ttu-id="93738-103">設定不是組件特定的旗標。</span><span class="sxs-lookup"><span data-stu-id="93738-103">Sets flags that are not assembly-specific.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93738-104">語法</span><span class="sxs-lookup"><span data-stu-id="93738-104">Syntax</span></span>  
  
```  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="93738-105">參數</span><span class="sxs-lookup"><span data-stu-id="93738-105">Parameters</span></span>  
 `afFlags`  
 <span data-ttu-id="93738-106">ALink 旗標。</span><span class="sxs-lookup"><span data-stu-id="93738-106">ALink flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="93738-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="93738-107">Return Value</span></span>  
 <span data-ttu-id="93738-108">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="93738-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93738-109">需求</span><span class="sxs-lookup"><span data-stu-id="93738-109">Requirements</span></span>  
 <span data-ttu-id="93738-110">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="93738-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93738-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93738-111">See also</span></span>
- [<span data-ttu-id="93738-112">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="93738-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="93738-113">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="93738-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="93738-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="93738-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
