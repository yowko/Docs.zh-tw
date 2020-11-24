---
title: EmitAssembly 方法
ms.date: 03/30/2017
api_name:
- IALink2.EmitAssembly
- EmitAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssembly
helpviewer_keywords:
- EmitAssembly method
ms.assetid: 605ff39e-e5cc-4bff-8196-e8d68a9715b9
topic_type:
- apiref
ms.openlocfilehash: b85b2576660f77eb901c504d398e8bc7909882f7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676370"
---
# <a name="emitassembly-method"></a><span data-ttu-id="20538-102">EmitAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="20538-102">EmitAssembly Method</span></span>

<span data-ttu-id="20538-103">建立元件。</span><span class="sxs-lookup"><span data-stu-id="20538-103">Creates the assembly.</span></span> <span data-ttu-id="20538-104">在所有其他檔案都關閉之後（元件檔除外），請呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="20538-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="20538-105">請勿在產生未系結的模組時呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="20538-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20538-106">語法</span><span class="sxs-lookup"><span data-stu-id="20538-106">Syntax</span></span>  
  
```cpp  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="20538-107">參數</span><span class="sxs-lookup"><span data-stu-id="20538-107">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="20538-108">元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="20538-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20538-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="20538-109">Return Value</span></span>  

 <span data-ttu-id="20538-110">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="20538-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20538-111">需求</span><span class="sxs-lookup"><span data-stu-id="20538-111">Requirements</span></span>  

 <span data-ttu-id="20538-112">需要 alink。h</span><span class="sxs-lookup"><span data-stu-id="20538-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20538-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20538-113">See also</span></span>

- [<span data-ttu-id="20538-114">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="20538-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="20538-115">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="20538-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="20538-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="20538-116">ALink API</span></span>](index.md)
