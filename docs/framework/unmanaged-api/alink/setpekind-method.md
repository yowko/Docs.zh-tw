---
title: SetPEKind 方法
ms.date: 03/30/2017
api_name:
- IALink2.SetPEKind
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetPEKind
helpviewer_keywords:
- SetPEKind method
ms.assetid: 050e77ee-3014-45c0-9e29-2ebe29347b0d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e568050a5cc94da865d656adc8a775024dab836c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500040"
---
# <a name="setpekind-method"></a><span data-ttu-id="ed911-102">SetPEKind 方法</span><span class="sxs-lookup"><span data-stu-id="ed911-102">SetPEKind Method</span></span>
<span data-ttu-id="ed911-103">決定可攜式執行檔的類型，特定電腦或機器無關。</span><span class="sxs-lookup"><span data-stu-id="ed911-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed911-104">語法</span><span class="sxs-lookup"><span data-stu-id="ed911-104">Syntax</span></span>  
  
```  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="ed911-105">參數</span><span class="sxs-lookup"><span data-stu-id="ed911-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="ed911-106">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="ed911-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="ed911-107">PE 型別為其設定的檔的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="ed911-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="ed911-108">可以是 NULL，如果`AssemblyID`不會指出未繫結的 netmodule。</span><span class="sxs-lookup"><span data-stu-id="ed911-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="ed911-109">PE 所指定的型別[CorPEKind 列舉](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="ed911-109">The type of PE, as indicated by the [CorPEKind Enumeration](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="ed911-110">目標電腦架構，NT 標頭中所示。</span><span class="sxs-lookup"><span data-stu-id="ed911-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed911-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="ed911-111">Return Value</span></span>  
 <span data-ttu-id="ed911-112">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="ed911-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed911-113">需求</span><span class="sxs-lookup"><span data-stu-id="ed911-113">Requirements</span></span>  
 <span data-ttu-id="ed911-114">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="ed911-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed911-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed911-115">See also</span></span>
- [<span data-ttu-id="ed911-116">GetPEKind 方法</span><span class="sxs-lookup"><span data-stu-id="ed911-116">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)
- [<span data-ttu-id="ed911-117">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="ed911-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="ed911-118">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="ed911-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="ed911-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="ed911-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
