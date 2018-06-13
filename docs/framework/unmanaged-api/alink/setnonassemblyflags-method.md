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
ms.openlocfilehash: 0399a135eddfd87342db63e107c8eea59a6e54d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401699"
---
# <a name="setnonassemblyflags-method"></a><span data-ttu-id="f537f-102">SetNonAssemblyFlags 方法</span><span class="sxs-lookup"><span data-stu-id="f537f-102">SetNonAssemblyFlags Method</span></span>
<span data-ttu-id="f537f-103">設定不是組件特定的旗標。</span><span class="sxs-lookup"><span data-stu-id="f537f-103">Sets flags that are not assembly-specific.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f537f-104">語法</span><span class="sxs-lookup"><span data-stu-id="f537f-104">Syntax</span></span>  
  
```  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f537f-105">參數</span><span class="sxs-lookup"><span data-stu-id="f537f-105">Parameters</span></span>  
 `afFlags`  
 <span data-ttu-id="f537f-106">ALink 旗標。</span><span class="sxs-lookup"><span data-stu-id="f537f-106">ALink flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f537f-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="f537f-107">Return Value</span></span>  
 <span data-ttu-id="f537f-108">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="f537f-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f537f-109">需求</span><span class="sxs-lookup"><span data-stu-id="f537f-109">Requirements</span></span>  
 <span data-ttu-id="f537f-110">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="f537f-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f537f-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f537f-111">See Also</span></span>  
 [<span data-ttu-id="f537f-112">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="f537f-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="f537f-113">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="f537f-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="f537f-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="f537f-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
