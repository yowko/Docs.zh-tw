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
ms.openlocfilehash: 4b985aeb97621e552e9e97581e67cae029d019ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405889"
---
# <a name="setpekind-method"></a><span data-ttu-id="477e5-102">SetPEKind 方法</span><span class="sxs-lookup"><span data-stu-id="477e5-102">SetPEKind Method</span></span>
<span data-ttu-id="477e5-103">決定可攜式執行檔的類型，特定電腦或電腦無關。</span><span class="sxs-lookup"><span data-stu-id="477e5-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="477e5-104">語法</span><span class="sxs-lookup"><span data-stu-id="477e5-104">Syntax</span></span>  
  
```  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
#### <a name="parameters"></a><span data-ttu-id="477e5-105">參數</span><span class="sxs-lookup"><span data-stu-id="477e5-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="477e5-106">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="477e5-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="477e5-107">PE 類型是設定的檔案的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="477e5-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="477e5-108">可以是 NULL，如果`AssemblyID`不會指出未繫結的 netmodule。</span><span class="sxs-lookup"><span data-stu-id="477e5-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="477e5-109">PE 所指定的型別[CorPEKind 列舉](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="477e5-109">The type of PE, as indicated by the [CorPEKind Enumeration](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="477e5-110">目標電腦架構，NT 標頭中所示。</span><span class="sxs-lookup"><span data-stu-id="477e5-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="477e5-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="477e5-111">Return Value</span></span>  
 <span data-ttu-id="477e5-112">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="477e5-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="477e5-113">需求</span><span class="sxs-lookup"><span data-stu-id="477e5-113">Requirements</span></span>  
 <span data-ttu-id="477e5-114">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="477e5-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="477e5-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="477e5-115">See Also</span></span>  
 [<span data-ttu-id="477e5-116">GetPEKind 方法</span><span class="sxs-lookup"><span data-stu-id="477e5-116">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)  
 [<span data-ttu-id="477e5-117">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="477e5-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="477e5-118">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="477e5-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="477e5-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="477e5-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
