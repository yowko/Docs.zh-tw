---
title: "SetPEKind 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.SetPEKind
api_location: alink.dll
api_type: COM
f1_keywords: SetPEKind
helpviewer_keywords: SetPEKind method
ms.assetid: 050e77ee-3014-45c0-9e29-2ebe29347b0d
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d511bcda2ab4e879c123d866b3f6c887173c1d2f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="setpekind-method"></a><span data-ttu-id="79b07-102">SetPEKind 方法</span><span class="sxs-lookup"><span data-stu-id="79b07-102">SetPEKind Method</span></span>
<span data-ttu-id="79b07-103">決定可攜式執行檔的類型，特定電腦或電腦無關。</span><span class="sxs-lookup"><span data-stu-id="79b07-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79b07-104">語法</span><span class="sxs-lookup"><span data-stu-id="79b07-104">Syntax</span></span>  
  
```  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
#### <a name="parameters"></a><span data-ttu-id="79b07-105">參數</span><span class="sxs-lookup"><span data-stu-id="79b07-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="79b07-106">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="79b07-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="79b07-107">PE 類型是設定的檔案的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="79b07-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="79b07-108">可以是 NULL，如果`AssemblyID`不會指出未繫結的 netmodule。</span><span class="sxs-lookup"><span data-stu-id="79b07-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="79b07-109">PE 所指定的型別[CorPEKind 列舉](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="79b07-109">The type of PE, as indicated by the [CorPEKind Enumeration](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="79b07-110">目標電腦架構，NT 標頭中所示。</span><span class="sxs-lookup"><span data-stu-id="79b07-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79b07-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="79b07-111">Return Value</span></span>  
 <span data-ttu-id="79b07-112">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="79b07-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79b07-113">需求</span><span class="sxs-lookup"><span data-stu-id="79b07-113">Requirements</span></span>  
 <span data-ttu-id="79b07-114">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="79b07-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79b07-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79b07-115">See Also</span></span>  
 [<span data-ttu-id="79b07-116">GetPEKind 方法</span><span class="sxs-lookup"><span data-stu-id="79b07-116">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)  
 [<span data-ttu-id="79b07-117">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="79b07-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="79b07-118">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="79b07-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="79b07-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="79b07-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
