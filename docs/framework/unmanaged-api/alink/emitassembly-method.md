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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a2adf53d1e29fda077cdcf7b79891f6271993109
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787589"
---
# <a name="emitassembly-method"></a><span data-ttu-id="5774e-102">EmitAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="5774e-102">EmitAssembly Method</span></span>
<span data-ttu-id="5774e-103">建立元件。</span><span class="sxs-lookup"><span data-stu-id="5774e-103">Creates the assembly.</span></span> <span data-ttu-id="5774e-104">在關閉所有其他檔案（元件檔案除外）之後，呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="5774e-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="5774e-105">產生未系結的模組時，請勿呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="5774e-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5774e-106">語法</span><span class="sxs-lookup"><span data-stu-id="5774e-106">Syntax</span></span>  
  
```cpp  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="5774e-107">參數</span><span class="sxs-lookup"><span data-stu-id="5774e-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="5774e-108">元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="5774e-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5774e-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="5774e-109">Return Value</span></span>  
 <span data-ttu-id="5774e-110">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="5774e-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5774e-111">需求</span><span class="sxs-lookup"><span data-stu-id="5774e-111">Requirements</span></span>  
 <span data-ttu-id="5774e-112">需要 alink. h</span><span class="sxs-lookup"><span data-stu-id="5774e-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5774e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5774e-113">See also</span></span>

- [<span data-ttu-id="5774e-114">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="5774e-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="5774e-115">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="5774e-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="5774e-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="5774e-116">ALink API</span></span>](index.md)
