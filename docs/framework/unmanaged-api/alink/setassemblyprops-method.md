---
title: "SetAssemblyProps 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.SetAssemblyProps
api_location: alink.dll
api_type: COM
f1_keywords: SetAssemblyProps
helpviewer_keywords: SetAssemblyProps method
ms.assetid: a3d7cf29-1414-49e6-8aae-9b3283c4f5f0
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae13daab0352ad4367c7ad6e06d6c12af23c75bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="51666-102">SetAssemblyProps 方法</span><span class="sxs-lookup"><span data-stu-id="51666-102">SetAssemblyProps Method</span></span>
<span data-ttu-id="51666-103">指定組件層級的屬性。</span><span class="sxs-lookup"><span data-stu-id="51666-103">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51666-104">語法</span><span class="sxs-lookup"><span data-stu-id="51666-104">Syntax</span></span>  
  
```  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="51666-105">參數</span><span class="sxs-lookup"><span data-stu-id="51666-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="51666-106">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="51666-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="51666-107">定義屬性的檔案。</span><span class="sxs-lookup"><span data-stu-id="51666-107">File that defines the property.</span></span> <span data-ttu-id="51666-108">可以是 NULL，如果`AssemblyID`不會指出未繫結的 netmodule。</span><span class="sxs-lookup"><span data-stu-id="51666-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="51666-109">指出修改的選項。</span><span class="sxs-lookup"><span data-stu-id="51666-109">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="51666-110">新的選項值。</span><span class="sxs-lookup"><span data-stu-id="51666-110">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="51666-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="51666-111">Return Value</span></span>  
 <span data-ttu-id="51666-112">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="51666-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51666-113">需求</span><span class="sxs-lookup"><span data-stu-id="51666-113">Requirements</span></span>  
 <span data-ttu-id="51666-114">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="51666-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51666-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="51666-115">See Also</span></span>  
 [<span data-ttu-id="51666-116">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="51666-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="51666-117">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="51666-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="51666-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="51666-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
