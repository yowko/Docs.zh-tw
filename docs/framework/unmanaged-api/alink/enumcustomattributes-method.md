---
title: "EnumCustomAttributes 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EnumCustomAttributes
- IALink.EnumCustomAttributes
api_location: alink.dll
api_type: COM
f1_keywords: EnumCustomAttributes
helpviewer_keywords: EnumCustomAttributes method
ms.assetid: 08dff60c-f01b-4050-8865-ea3f95361c9f
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: febaba5155753e9d60a3708582f4f58bd7861ec7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="4db64-102">EnumCustomAttributes 方法</span><span class="sxs-lookup"><span data-stu-id="4db64-102">EnumCustomAttributes Method</span></span>
<span data-ttu-id="4db64-103">擷取組件層級自訂的屬性。</span><span class="sxs-lookup"><span data-stu-id="4db64-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4db64-104">語法</span><span class="sxs-lookup"><span data-stu-id="4db64-104">Syntax</span></span>  
  
```  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4db64-105">參數</span><span class="sxs-lookup"><span data-stu-id="4db64-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="4db64-106">列舉值的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="4db64-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="4db64-107">要列舉的屬性類型。</span><span class="sxs-lookup"><span data-stu-id="4db64-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="4db64-108">使用`mdTokenNill`所有屬性。</span><span class="sxs-lookup"><span data-stu-id="4db64-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="4db64-109">接收權杖的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="4db64-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="4db64-110">指定的大小`rCustomValues`陣列。</span><span class="sxs-lookup"><span data-stu-id="4db64-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="4db64-111">（選擇性） 接收語彙基元值的計數。</span><span class="sxs-lookup"><span data-stu-id="4db64-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4db64-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="4db64-112">Return Value</span></span>  
 <span data-ttu-id="4db64-113">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="4db64-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4db64-114">需求</span><span class="sxs-lookup"><span data-stu-id="4db64-114">Requirements</span></span>  
 <span data-ttu-id="4db64-115">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="4db64-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4db64-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4db64-116">See Also</span></span>  
 [<span data-ttu-id="4db64-117">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="4db64-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="4db64-118">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="4db64-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="4db64-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="4db64-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
