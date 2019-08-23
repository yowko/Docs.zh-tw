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
ms.openlocfilehash: 7188c516d3d0a5192251697ec743e9d41f8d9072
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913733"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a><span data-ttu-id="1c015-102">CorSymSearchPolicyAttributes 列舉</span><span class="sxs-lookup"><span data-stu-id="1c015-102">CorSymSearchPolicyAttributes Enumeration</span></span>
<span data-ttu-id="1c015-103">指定搜尋符號讀取器時要使用的原則。</span><span class="sxs-lookup"><span data-stu-id="1c015-103">Specifies the policy to be used when doing a search for a symbol reader.</span></span> <span data-ttu-id="1c015-104">這些常數是由[ISymUnmanagedBinder2:: GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)和[ISymUnmanagedBinder3:: GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)方法所使用。</span><span class="sxs-lookup"><span data-stu-id="1c015-104">These constants are used by the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) and [ISymUnmanagedBinder3::GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1c015-105">從不受信任的來源開啟程式資料庫 (PDB) 檔案會有安全性風險。</span><span class="sxs-lookup"><span data-stu-id="1c015-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c015-106">語法</span><span class="sxs-lookup"><span data-stu-id="1c015-106">Syntax</span></span>  
  
```cpp  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,       
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //      
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a><span data-ttu-id="1c015-107">成員</span><span class="sxs-lookup"><span data-stu-id="1c015-107">Members</span></span>  
  
|<span data-ttu-id="1c015-108">成員</span><span class="sxs-lookup"><span data-stu-id="1c015-108">Member</span></span>|<span data-ttu-id="1c015-109">描述</span><span class="sxs-lookup"><span data-stu-id="1c015-109">Description</span></span>|  
|------------|-----------------|  
|`AllowRegistryAccess`|<span data-ttu-id="1c015-110">查詢登錄中的符號搜尋路徑。</span><span class="sxs-lookup"><span data-stu-id="1c015-110">Queries the registry for symbol search paths.</span></span>|  
|`AllowSymbolServerAccess`|<span data-ttu-id="1c015-111">存取符號伺服器。</span><span class="sxs-lookup"><span data-stu-id="1c015-111">Accesses a symbol server.</span></span>|  
|`AllowOriginalPathAccess`|<span data-ttu-id="1c015-112">搜尋在 Debug 目錄中指定的路徑。</span><span class="sxs-lookup"><span data-stu-id="1c015-112">Searches the path specified in the Debug directory.</span></span>|  
|`AllowReferencePathAccess`|<span data-ttu-id="1c015-113">在 .exe 檔案所在的位置搜尋 PDB。</span><span class="sxs-lookup"><span data-stu-id="1c015-113">Searches for the PDB in the place where the .exe file is.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1c015-114">需求</span><span class="sxs-lookup"><span data-stu-id="1c015-114">Requirements</span></span>  
 <span data-ttu-id="1c015-115">**標頭：** CorSym .idl, CorSym。h</span><span class="sxs-lookup"><span data-stu-id="1c015-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c015-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c015-116">See also</span></span>

- [<span data-ttu-id="1c015-117">診斷符號存放區列舉</span><span class="sxs-lookup"><span data-stu-id="1c015-117">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
