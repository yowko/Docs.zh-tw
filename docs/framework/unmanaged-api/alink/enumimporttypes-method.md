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
ms.openlocfilehash: df6efbc86ff958cb8a715c81f86ea1112629fe67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="6d960-102">EnumImportTypes 方法</span><span class="sxs-lookup"><span data-stu-id="6d960-102">EnumImportTypes Method</span></span>
<span data-ttu-id="6d960-103">列舉每個範圍中的每個型別。</span><span class="sxs-lookup"><span data-stu-id="6d960-103">Enumerates each type in each scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d960-104">語法</span><span class="sxs-lookup"><span data-stu-id="6d960-104">Syntax</span></span>  
  
```  
HRESULT EnumImportTypes(  
    HALINKENUM   hEnum,  
    DWORD        dwMax,  
    mdTypeDef    aTypeDefs[],  
    DWORD*       pdwCount  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6d960-105">參數</span><span class="sxs-lookup"><span data-stu-id="6d960-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="6d960-106">列舉值的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="6d960-106">Handle for enumerator.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="6d960-107">擷取類型的最大數目。</span><span class="sxs-lookup"><span data-stu-id="6d960-107">Maximum number of types to retrieve.</span></span>  
  
 `aTypeDefs`  
 <span data-ttu-id="6d960-108">將收到輸入權杖，不能超過`dwMax`。</span><span class="sxs-lookup"><span data-stu-id="6d960-108">Recieves type tokens, not to exceed `dwMax`.</span></span>  
  
 `pdwCount`  
 <span data-ttu-id="6d960-109">接收的類型中實際數目`aTypeDefs`。</span><span class="sxs-lookup"><span data-stu-id="6d960-109">Receives actual number of type in `aTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d960-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="6d960-110">Return Value</span></span>  
 <span data-ttu-id="6d960-111">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="6d960-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d960-112">需求</span><span class="sxs-lookup"><span data-stu-id="6d960-112">Requirements</span></span>  
 <span data-ttu-id="6d960-113">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="6d960-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d960-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d960-114">See Also</span></span>  
 [<span data-ttu-id="6d960-115">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="6d960-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="6d960-116">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="6d960-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="6d960-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="6d960-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
