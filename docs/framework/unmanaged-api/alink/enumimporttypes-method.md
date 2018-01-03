---
title: "EnumImportTypes 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EnumImportTypes
- IALink.EnumImportTypes
api_location: alink.dll
api_type: COM
f1_keywords: EnumImportTypes
helpviewer_keywords: EnumImportTypes method
ms.assetid: 83a0e4e7-ec06-40cb-9b63-700b9695bb04
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 08644816d3fa11ade5a8ebee1573e8f66d526101
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="4b17c-102">EnumImportTypes 方法</span><span class="sxs-lookup"><span data-stu-id="4b17c-102">EnumImportTypes Method</span></span>
<span data-ttu-id="4b17c-103">列舉每個範圍中的每個型別。</span><span class="sxs-lookup"><span data-stu-id="4b17c-103">Enumerates each type in each scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b17c-104">語法</span><span class="sxs-lookup"><span data-stu-id="4b17c-104">Syntax</span></span>  
  
```  
HRESULT EnumImportTypes(  
    HALINKENUM   hEnum,  
    DWORD        dwMax,  
    mdTypeDef    aTypeDefs[],  
    DWORD*       pdwCount  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4b17c-105">參數</span><span class="sxs-lookup"><span data-stu-id="4b17c-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="4b17c-106">列舉值的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="4b17c-106">Handle for enumerator.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="4b17c-107">擷取類型的最大數目。</span><span class="sxs-lookup"><span data-stu-id="4b17c-107">Maximum number of types to retrieve.</span></span>  
  
 `aTypeDefs`  
 <span data-ttu-id="4b17c-108">將收到輸入權杖，不能超過`dwMax`。</span><span class="sxs-lookup"><span data-stu-id="4b17c-108">Recieves type tokens, not to exceed `dwMax`.</span></span>  
  
 `pdwCount`  
 <span data-ttu-id="4b17c-109">接收的類型中實際數目`aTypeDefs`。</span><span class="sxs-lookup"><span data-stu-id="4b17c-109">Receives actual number of type in `aTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4b17c-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="4b17c-110">Return Value</span></span>  
 <span data-ttu-id="4b17c-111">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="4b17c-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b17c-112">需求</span><span class="sxs-lookup"><span data-stu-id="4b17c-112">Requirements</span></span>  
 <span data-ttu-id="4b17c-113">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="4b17c-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b17c-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="4b17c-114">See Also</span></span>  
 [<span data-ttu-id="4b17c-115">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="4b17c-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="4b17c-116">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="4b17c-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="4b17c-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="4b17c-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
