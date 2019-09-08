---
title: CloseAssembly 方法
ms.date: 03/30/2017
api_name:
- IALink.CloseAssembly
- CloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseAssembly
helpviewer_keywords:
- CloseAssembly method
ms.assetid: f66a43bc-a5c5-4190-acbe-63fd27640634
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b7828c86018724bb934de99cab4617f9885fdca6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787614"
---
# <a name="closeassembly-method"></a><span data-ttu-id="24ad8-102">CloseAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="24ad8-102">CloseAssembly Method</span></span>
<span data-ttu-id="24ad8-103">完成元件作業。</span><span class="sxs-lookup"><span data-stu-id="24ad8-103">Finalizes assembly operations.</span></span> <span data-ttu-id="24ad8-104">在開始新元件或解除系結模組之前，請先呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="24ad8-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24ad8-105">語法</span><span class="sxs-lookup"><span data-stu-id="24ad8-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="24ad8-106">參數</span><span class="sxs-lookup"><span data-stu-id="24ad8-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="24ad8-107">元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="24ad8-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24ad8-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="24ad8-108">Return Value</span></span>  
 <span data-ttu-id="24ad8-109">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="24ad8-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24ad8-110">需求</span><span class="sxs-lookup"><span data-stu-id="24ad8-110">Requirements</span></span>  
 <span data-ttu-id="24ad8-111">需要 alink. h。</span><span class="sxs-lookup"><span data-stu-id="24ad8-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24ad8-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24ad8-112">See also</span></span>

- [<span data-ttu-id="24ad8-113">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="24ad8-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="24ad8-114">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="24ad8-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="24ad8-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="24ad8-115">ALink API</span></span>](index.md)
