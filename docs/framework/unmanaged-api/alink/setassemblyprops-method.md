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
ms.openlocfilehash: dc9ca5d9533a6c4a297155a47ac0061f1232d242
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481097"
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="425e0-102">SetAssemblyProps 方法</span><span class="sxs-lookup"><span data-stu-id="425e0-102">SetAssemblyProps Method</span></span>
<span data-ttu-id="425e0-103">會指派組件層級屬性。</span><span class="sxs-lookup"><span data-stu-id="425e0-103">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="425e0-104">語法</span><span class="sxs-lookup"><span data-stu-id="425e0-104">Syntax</span></span>  
  
```  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="425e0-105">參數</span><span class="sxs-lookup"><span data-stu-id="425e0-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="425e0-106">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="425e0-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="425e0-107">定義屬性的檔案。</span><span class="sxs-lookup"><span data-stu-id="425e0-107">File that defines the property.</span></span> <span data-ttu-id="425e0-108">可以是 NULL，如果`AssemblyID`不會指出未繫結的 netmodule。</span><span class="sxs-lookup"><span data-stu-id="425e0-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="425e0-109">表示修改的選項。</span><span class="sxs-lookup"><span data-stu-id="425e0-109">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="425e0-110">新的選項值。</span><span class="sxs-lookup"><span data-stu-id="425e0-110">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="425e0-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="425e0-111">Return Value</span></span>  
 <span data-ttu-id="425e0-112">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="425e0-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="425e0-113">需求</span><span class="sxs-lookup"><span data-stu-id="425e0-113">Requirements</span></span>  
 <span data-ttu-id="425e0-114">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="425e0-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="425e0-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="425e0-115">See also</span></span>
- [<span data-ttu-id="425e0-116">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="425e0-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="425e0-117">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="425e0-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="425e0-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="425e0-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
