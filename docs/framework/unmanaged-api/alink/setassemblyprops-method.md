---
title: SetAssemblyProps 方法
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyProps
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method
ms.assetid: a3d7cf29-1414-49e6-8aae-9b3283c4f5f0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 589bd7b2132693c89dc10ae1a5c8d0bf52ed481e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218988"
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="bd66d-102">SetAssemblyProps 方法</span><span class="sxs-lookup"><span data-stu-id="bd66d-102">SetAssemblyProps Method</span></span>
<span data-ttu-id="bd66d-103">會指派組件層級屬性。</span><span class="sxs-lookup"><span data-stu-id="bd66d-103">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd66d-104">語法</span><span class="sxs-lookup"><span data-stu-id="bd66d-104">Syntax</span></span>  
  
```  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd66d-105">參數</span><span class="sxs-lookup"><span data-stu-id="bd66d-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="bd66d-106">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="bd66d-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="bd66d-107">定義屬性的檔案。</span><span class="sxs-lookup"><span data-stu-id="bd66d-107">File that defines the property.</span></span> <span data-ttu-id="bd66d-108">可以是 NULL，如果`AssemblyID`不會指出未繫結的 netmodule。</span><span class="sxs-lookup"><span data-stu-id="bd66d-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="bd66d-109">表示修改的選項。</span><span class="sxs-lookup"><span data-stu-id="bd66d-109">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="bd66d-110">新的選項值。</span><span class="sxs-lookup"><span data-stu-id="bd66d-110">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd66d-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="bd66d-111">Return Value</span></span>  
 <span data-ttu-id="bd66d-112">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="bd66d-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd66d-113">需求</span><span class="sxs-lookup"><span data-stu-id="bd66d-113">Requirements</span></span>  
 <span data-ttu-id="bd66d-114">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="bd66d-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd66d-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd66d-115">See also</span></span>

- [<span data-ttu-id="bd66d-116">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="bd66d-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="bd66d-117">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="bd66d-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="bd66d-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="bd66d-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
