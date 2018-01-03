---
title: "CorSymSearchPolicyAttributes 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorSymSearchPolicyAttributes
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSymSearchPolicyAttributes
helpviewer_keywords: CorSymSearchPolicyAttributes enumeration [.NET Framework debugging]
ms.assetid: 03abde84-930a-49d3-bac3-23abb34a0184
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bc1bef8c393a7778c194b2d4d45c3abdb583fecf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="corsymsearchpolicyattributes-enumeration"></a><span data-ttu-id="ba3e3-102">CorSymSearchPolicyAttributes 列舉</span><span class="sxs-lookup"><span data-stu-id="ba3e3-102">CorSymSearchPolicyAttributes Enumeration</span></span>
<span data-ttu-id="ba3e3-103">指定要進行搜尋的符號讀取器時使用的原則。</span><span class="sxs-lookup"><span data-stu-id="ba3e3-103">Specifies the policy to be used when doing a search for a symbol reader.</span></span> <span data-ttu-id="ba3e3-104">這些常數由[isymunmanagedbinder2:: Getreaderforfile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)和[isymunmanagedbinder3:: Getreaderfromcallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="ba3e3-104">These constants are used by the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) and [ISymUnmanagedBinder3::GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) methods.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ba3e3-105">它是從受信任的來源開啟程式資料庫 (PDB) 檔的安全性風險。</span><span class="sxs-lookup"><span data-stu-id="ba3e3-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba3e3-106">語法</span><span class="sxs-lookup"><span data-stu-id="ba3e3-106">Syntax</span></span>  
  
```  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,       
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //      
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a><span data-ttu-id="ba3e3-107">成員</span><span class="sxs-lookup"><span data-stu-id="ba3e3-107">Members</span></span>  
  
|<span data-ttu-id="ba3e3-108">成員</span><span class="sxs-lookup"><span data-stu-id="ba3e3-108">Member</span></span>|<span data-ttu-id="ba3e3-109">描述</span><span class="sxs-lookup"><span data-stu-id="ba3e3-109">Description</span></span>|  
|------------|-----------------|  
|`AllowRegistryAccess`|<span data-ttu-id="ba3e3-110">查詢符號搜尋路徑的登錄。</span><span class="sxs-lookup"><span data-stu-id="ba3e3-110">Queries the registry for symbol search paths.</span></span>|  
|`AllowSymbolServerAccess`|<span data-ttu-id="ba3e3-111">存取符號伺服器。</span><span class="sxs-lookup"><span data-stu-id="ba3e3-111">Accesses a symbol server.</span></span>|  
|`AllowOriginalPathAccess`|<span data-ttu-id="ba3e3-112">搜尋偵錯目錄中指定的路徑。</span><span class="sxs-lookup"><span data-stu-id="ba3e3-112">Searches the path specified in the Debug directory.</span></span>|  
|`AllowReferencePathAccess`|<span data-ttu-id="ba3e3-113">搜尋 PDB 中的.exe 檔案所在的位置。</span><span class="sxs-lookup"><span data-stu-id="ba3e3-113">Searches for the PDB in the place where the .exe file is.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ba3e3-114">需求</span><span class="sxs-lookup"><span data-stu-id="ba3e3-114">Requirements</span></span>  
 <span data-ttu-id="ba3e3-115">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ba3e3-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba3e3-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="ba3e3-116">See Also</span></span>  
 [<span data-ttu-id="ba3e3-117">診斷符號存放區列舉</span><span class="sxs-lookup"><span data-stu-id="ba3e3-117">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
