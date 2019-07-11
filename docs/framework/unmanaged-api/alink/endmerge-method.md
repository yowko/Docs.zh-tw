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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8daf76e50b4c584115a55936aa9336c95a3669ec
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742075"
---
# <a name="endmerge-method"></a><span data-ttu-id="cd224-102">EndMerge 方法</span><span class="sxs-lookup"><span data-stu-id="cd224-102">EndMerge Method</span></span>
<span data-ttu-id="cd224-103">表示所有自訂屬性，已合併至發出範圍。</span><span class="sxs-lookup"><span data-stu-id="cd224-103">Indicates that all custom attributes have been merged into the emit scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd224-104">語法</span><span class="sxs-lookup"><span data-stu-id="cd224-104">Syntax</span></span>  
  
```cpp  
HRESULT EndMerge(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd224-105">參數</span><span class="sxs-lookup"><span data-stu-id="cd224-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="cd224-106">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="cd224-106">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd224-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="cd224-107">Return Value</span></span>  
 <span data-ttu-id="cd224-108">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="cd224-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd224-109">需求</span><span class="sxs-lookup"><span data-stu-id="cd224-109">Requirements</span></span>  
 <span data-ttu-id="cd224-110">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="cd224-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd224-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd224-111">See also</span></span>

- [<span data-ttu-id="cd224-112">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="cd224-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="cd224-113">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="cd224-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="cd224-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="cd224-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
