---
title: EndMerge 方法
ms.date: 03/30/2017
api_name:
- IALink.EndMerge
- EndMerge
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EndMerge
helpviewer_keywords:
- EndMerge method
ms.assetid: 1d03bb15-a2c8-4a04-8fc6-b126c89c3778
topic_type:
- apiref
ms.openlocfilehash: ed4ac7b12caa0dd78b79554258de62b8752553e0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684924"
---
# <a name="endmerge-method"></a><span data-ttu-id="ce19d-102">EndMerge 方法</span><span class="sxs-lookup"><span data-stu-id="ce19d-102">EndMerge Method</span></span>

<span data-ttu-id="ce19d-103">指出所有自訂屬性都已合併到發出範圍中。</span><span class="sxs-lookup"><span data-stu-id="ce19d-103">Indicates that all custom attributes have been merged into the emit scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce19d-104">語法</span><span class="sxs-lookup"><span data-stu-id="ce19d-104">Syntax</span></span>  
  
```cpp  
HRESULT EndMerge(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce19d-105">參數</span><span class="sxs-lookup"><span data-stu-id="ce19d-105">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="ce19d-106">元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="ce19d-106">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ce19d-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="ce19d-107">Return Value</span></span>  

 <span data-ttu-id="ce19d-108">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="ce19d-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce19d-109">需求</span><span class="sxs-lookup"><span data-stu-id="ce19d-109">Requirements</span></span>  

 <span data-ttu-id="ce19d-110">需要 alink。h</span><span class="sxs-lookup"><span data-stu-id="ce19d-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce19d-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce19d-111">See also</span></span>

- [<span data-ttu-id="ce19d-112">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="ce19d-112">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="ce19d-113">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="ce19d-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="ce19d-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="ce19d-114">ALink API</span></span>](index.md)
