---
title: CorSymSearchPolicyAttributes 列舉
ms.date: 03/30/2017
api_name:
- CorSymSearchPolicyAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymSearchPolicyAttributes
helpviewer_keywords:
- CorSymSearchPolicyAttributes enumeration [.NET Framework debugging]
ms.assetid: 03abde84-930a-49d3-bac3-23abb34a0184
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a9b0f085820bac12638c0310ab23b2eafacb23b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186169"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a><span data-ttu-id="97390-102">CorSymSearchPolicyAttributes 列舉</span><span class="sxs-lookup"><span data-stu-id="97390-102">CorSymSearchPolicyAttributes Enumeration</span></span>
<span data-ttu-id="97390-103">指定要在進行搜尋的符號讀取器時使用的原則。</span><span class="sxs-lookup"><span data-stu-id="97390-103">Specifies the policy to be used when doing a search for a symbol reader.</span></span> <span data-ttu-id="97390-104">這些常數由[ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)並[ISymUnmanagedBinder3::GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="97390-104">These constants are used by the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) and [ISymUnmanagedBinder3::GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) methods.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="97390-105">它是從受信任的來源開啟程式資料庫 (PDB) 檔的安全性風險。</span><span class="sxs-lookup"><span data-stu-id="97390-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97390-106">語法</span><span class="sxs-lookup"><span data-stu-id="97390-106">Syntax</span></span>  
  
```  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,       
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //      
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a><span data-ttu-id="97390-107">成員</span><span class="sxs-lookup"><span data-stu-id="97390-107">Members</span></span>  
  
|<span data-ttu-id="97390-108">成員</span><span class="sxs-lookup"><span data-stu-id="97390-108">Member</span></span>|<span data-ttu-id="97390-109">描述</span><span class="sxs-lookup"><span data-stu-id="97390-109">Description</span></span>|  
|------------|-----------------|  
|`AllowRegistryAccess`|<span data-ttu-id="97390-110">查詢符號搜尋路徑的登錄。</span><span class="sxs-lookup"><span data-stu-id="97390-110">Queries the registry for symbol search paths.</span></span>|  
|`AllowSymbolServerAccess`|<span data-ttu-id="97390-111">存取符號伺服器。</span><span class="sxs-lookup"><span data-stu-id="97390-111">Accesses a symbol server.</span></span>|  
|`AllowOriginalPathAccess`|<span data-ttu-id="97390-112">搜尋指定的偵錯目錄中的路徑。</span><span class="sxs-lookup"><span data-stu-id="97390-112">Searches the path specified in the Debug directory.</span></span>|  
|`AllowReferencePathAccess`|<span data-ttu-id="97390-113">搜尋 PDB 中的.exe 檔案所在的位置。</span><span class="sxs-lookup"><span data-stu-id="97390-113">Searches for the PDB in the place where the .exe file is.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="97390-114">需求</span><span class="sxs-lookup"><span data-stu-id="97390-114">Requirements</span></span>  
 <span data-ttu-id="97390-115">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="97390-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97390-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97390-116">See also</span></span>

- [<span data-ttu-id="97390-117">診斷符號存放區列舉</span><span class="sxs-lookup"><span data-stu-id="97390-117">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
