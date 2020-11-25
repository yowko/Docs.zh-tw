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
ms.openlocfilehash: 4e8aeef3520c4d5c9735b2c8975ac1e39470ba93
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717015"
---
# <a name="closeassembly-method"></a><span data-ttu-id="f9b7e-102">CloseAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="f9b7e-102">CloseAssembly Method</span></span>

<span data-ttu-id="f9b7e-103">完成元件作業。</span><span class="sxs-lookup"><span data-stu-id="f9b7e-103">Finalizes assembly operations.</span></span> <span data-ttu-id="f9b7e-104">請先呼叫這個方法，再開始新的元件或未系結的模組。</span><span class="sxs-lookup"><span data-stu-id="f9b7e-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9b7e-105">語法</span><span class="sxs-lookup"><span data-stu-id="f9b7e-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9b7e-106">參數</span><span class="sxs-lookup"><span data-stu-id="f9b7e-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="f9b7e-107">元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="f9b7e-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9b7e-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="f9b7e-108">Return Value</span></span>  

 <span data-ttu-id="f9b7e-109">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="f9b7e-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9b7e-110">需求</span><span class="sxs-lookup"><span data-stu-id="f9b7e-110">Requirements</span></span>  

 <span data-ttu-id="f9b7e-111">需要 alink. h。</span><span class="sxs-lookup"><span data-stu-id="f9b7e-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9b7e-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9b7e-112">See also</span></span>

- [<span data-ttu-id="f9b7e-113">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="f9b7e-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="f9b7e-114">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="f9b7e-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="f9b7e-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="f9b7e-115">ALink API</span></span>](index.md)
