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
ms.openlocfilehash: 0cd451854d4dbb3b243339efdc33d7dcd7860eb7
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420600"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a><span data-ttu-id="28a21-102">CorSymSearchPolicyAttributes 列舉</span><span class="sxs-lookup"><span data-stu-id="28a21-102">CorSymSearchPolicyAttributes Enumeration</span></span>
<span data-ttu-id="28a21-103">指定搜尋符號讀取器時要使用的原則。</span><span class="sxs-lookup"><span data-stu-id="28a21-103">Specifies the policy to be used when doing a search for a symbol reader.</span></span> <span data-ttu-id="28a21-104">這些常數是由[ISymUnmanagedBinder2：： GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)和[ISymUnmanagedBinder3：： GetReaderFromCallback](isymunmanagedbinder3-getreaderfromcallback-method.md)方法所使用。</span><span class="sxs-lookup"><span data-stu-id="28a21-104">These constants are used by the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) and [ISymUnmanagedBinder3::GetReaderFromCallback](isymunmanagedbinder3-getreaderfromcallback-method.md) methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="28a21-105">從不受信任的來源開啟程式資料庫（PDB）檔案會有安全性風險。</span><span class="sxs-lookup"><span data-stu-id="28a21-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28a21-106">語法</span><span class="sxs-lookup"><span data-stu-id="28a21-106">Syntax</span></span>  
  
```cpp  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a><span data-ttu-id="28a21-107">成員</span><span class="sxs-lookup"><span data-stu-id="28a21-107">Members</span></span>  
  
|<span data-ttu-id="28a21-108">成員</span><span class="sxs-lookup"><span data-stu-id="28a21-108">Member</span></span>|<span data-ttu-id="28a21-109">說明</span><span class="sxs-lookup"><span data-stu-id="28a21-109">Description</span></span>|  
|------------|-----------------|  
|`AllowRegistryAccess`|<span data-ttu-id="28a21-110">查詢登錄中的符號搜尋路徑。</span><span class="sxs-lookup"><span data-stu-id="28a21-110">Queries the registry for symbol search paths.</span></span>|  
|`AllowSymbolServerAccess`|<span data-ttu-id="28a21-111">存取符號伺服器。</span><span class="sxs-lookup"><span data-stu-id="28a21-111">Accesses a symbol server.</span></span>|  
|`AllowOriginalPathAccess`|<span data-ttu-id="28a21-112">搜尋在 Debug 目錄中指定的路徑。</span><span class="sxs-lookup"><span data-stu-id="28a21-112">Searches the path specified in the Debug directory.</span></span>|  
|`AllowReferencePathAccess`|<span data-ttu-id="28a21-113">在 .exe 檔案所在的位置搜尋 PDB。</span><span class="sxs-lookup"><span data-stu-id="28a21-113">Searches for the PDB in the place where the .exe file is.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="28a21-114">需求</span><span class="sxs-lookup"><span data-stu-id="28a21-114">Requirements</span></span>  
 <span data-ttu-id="28a21-115">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="28a21-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28a21-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28a21-116">See also</span></span>

- [<span data-ttu-id="28a21-117">診斷符號存放區列舉</span><span class="sxs-lookup"><span data-stu-id="28a21-117">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)
