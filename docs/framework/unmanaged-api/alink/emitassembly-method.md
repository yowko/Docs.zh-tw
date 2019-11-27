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
ms.openlocfilehash: 6bbe5db75ded15f32a6ff3564e1116d40a745a65
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446530"
---
# <a name="emitassembly-method"></a><span data-ttu-id="b62ab-102">EmitAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="b62ab-102">EmitAssembly Method</span></span>
<span data-ttu-id="b62ab-103">建立元件。</span><span class="sxs-lookup"><span data-stu-id="b62ab-103">Creates the assembly.</span></span> <span data-ttu-id="b62ab-104">在關閉所有其他檔案（元件檔案除外）之後，呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="b62ab-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="b62ab-105">產生未系結的模組時，請勿呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="b62ab-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b62ab-106">語法</span><span class="sxs-lookup"><span data-stu-id="b62ab-106">Syntax</span></span>  
  
```cpp  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="b62ab-107">參數</span><span class="sxs-lookup"><span data-stu-id="b62ab-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="b62ab-108">元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="b62ab-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b62ab-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="b62ab-109">Return Value</span></span>  
 <span data-ttu-id="b62ab-110">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="b62ab-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b62ab-111">需求</span><span class="sxs-lookup"><span data-stu-id="b62ab-111">Requirements</span></span>  
 <span data-ttu-id="b62ab-112">需要 alink. h</span><span class="sxs-lookup"><span data-stu-id="b62ab-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b62ab-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b62ab-113">See also</span></span>

- [<span data-ttu-id="b62ab-114">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="b62ab-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="b62ab-115">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="b62ab-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="b62ab-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="b62ab-116">ALink API</span></span>](index.md)
