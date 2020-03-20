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
ms.openlocfilehash: 786e53d43ecde0bc3a97fadb77184d25d41430bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178341"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a><span data-ttu-id="8c0d0-102">CorSymSearchPolicyAttributes 列舉</span><span class="sxs-lookup"><span data-stu-id="8c0d0-102">CorSymSearchPolicyAttributes Enumeration</span></span>
<span data-ttu-id="8c0d0-103">指定在搜索符號讀取器時要使用的策略。</span><span class="sxs-lookup"><span data-stu-id="8c0d0-103">Specifies the policy to be used when doing a search for a symbol reader.</span></span> <span data-ttu-id="8c0d0-104">這些常量由[ISymUn 託管 Binder2：：getReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)和[ISymUn託管 Binder3：：getReader 來自回檔](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)方法使用。</span><span class="sxs-lookup"><span data-stu-id="8c0d0-104">These constants are used by the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) and [ISymUnmanagedBinder3::GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8c0d0-105">從不受信任的源打開程式資料庫 （PDB） 檔存在安全風險。</span><span class="sxs-lookup"><span data-stu-id="8c0d0-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c0d0-106">語法</span><span class="sxs-lookup"><span data-stu-id="8c0d0-106">Syntax</span></span>  
  
```cpp  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a><span data-ttu-id="8c0d0-107">成員</span><span class="sxs-lookup"><span data-stu-id="8c0d0-107">Members</span></span>  
  
|<span data-ttu-id="8c0d0-108">member</span><span class="sxs-lookup"><span data-stu-id="8c0d0-108">Member</span></span>|<span data-ttu-id="8c0d0-109">描述</span><span class="sxs-lookup"><span data-stu-id="8c0d0-109">Description</span></span>|  
|------------|-----------------|  
|`AllowRegistryAccess`|<span data-ttu-id="8c0d0-110">查詢符號搜索路徑的註冊表。</span><span class="sxs-lookup"><span data-stu-id="8c0d0-110">Queries the registry for symbol search paths.</span></span>|  
|`AllowSymbolServerAccess`|<span data-ttu-id="8c0d0-111">訪問符號伺服器。</span><span class="sxs-lookup"><span data-stu-id="8c0d0-111">Accesses a symbol server.</span></span>|  
|`AllowOriginalPathAccess`|<span data-ttu-id="8c0d0-112">搜索調試目錄中指定的路徑。</span><span class="sxs-lookup"><span data-stu-id="8c0d0-112">Searches the path specified in the Debug directory.</span></span>|  
|`AllowReferencePathAccess`|<span data-ttu-id="8c0d0-113">在 .exe 檔所在的位置搜索 PDB。</span><span class="sxs-lookup"><span data-stu-id="8c0d0-113">Searches for the PDB in the place where the .exe file is.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8c0d0-114">需求</span><span class="sxs-lookup"><span data-stu-id="8c0d0-114">Requirements</span></span>  
 <span data-ttu-id="8c0d0-115">**標題：** 科西姆.伊德爾，科西姆.h</span><span class="sxs-lookup"><span data-stu-id="8c0d0-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c0d0-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c0d0-116">See also</span></span>

- [<span data-ttu-id="8c0d0-117">診斷符號存放區列舉</span><span class="sxs-lookup"><span data-stu-id="8c0d0-117">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
