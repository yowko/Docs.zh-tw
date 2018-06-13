---
title: ISymUnmanagedWriter4 介面
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e8478aed662142b9ff4b73f9cb192f8d2306e2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429682"
---
# <a name="isymunmanagedwriter4-interface"></a><span data-ttu-id="583b6-102">ISymUnmanagedWriter4 介面</span><span class="sxs-lookup"><span data-stu-id="583b6-102">ISymUnmanagedWriter4 Interface</span></span>
<span data-ttu-id="583b6-103">ISymUnmanagedWriter4 介面。</span><span class="sxs-lookup"><span data-stu-id="583b6-103">ISymUnmanagedWriter4 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="583b6-104">語法</span><span class="sxs-lookup"><span data-stu-id="583b6-104">Syntax</span></span>  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a><span data-ttu-id="583b6-105">方法</span><span class="sxs-lookup"><span data-stu-id="583b6-105">Methods</span></span>  
 <span data-ttu-id="583b6-106">這個介面包含下列方法：</span><span class="sxs-lookup"><span data-stu-id="583b6-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="583b6-107">方法</span><span class="sxs-lookup"><span data-stu-id="583b6-107">Method</span></span>|<span data-ttu-id="583b6-108">描述</span><span class="sxs-lookup"><span data-stu-id="583b6-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="583b6-109">GetDebugInfoWithPadding 方法</span><span class="sxs-lookup"><span data-stu-id="583b6-109">GetDebugInfoWithPadding Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|<span data-ttu-id="583b6-110">函式與相同[GetDebugInfo 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md)不同之處在於路徑字串以下列結束的 null 字元的固定的大小，讓字串資料的零填補`MAX_PATH`。</span><span class="sxs-lookup"><span data-stu-id="583b6-110">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="583b6-111">如果路徑字串長度本身是填補只取得小於`MAX_PATH`。</span><span class="sxs-lookup"><span data-stu-id="583b6-111">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span><br /><br /> <span data-ttu-id="583b6-112">這可讓您更輕鬆地撰寫工具類型的差異 PE 檔案。</span><span class="sxs-lookup"><span data-stu-id="583b6-112">This makes it easier to write tools that difference PE files.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="583b6-113">需求</span><span class="sxs-lookup"><span data-stu-id="583b6-113">Requirements</span></span>  
 <span data-ttu-id="583b6-114">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="583b6-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="583b6-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="583b6-115">See Also</span></span>  
 [<span data-ttu-id="583b6-116">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="583b6-116">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="583b6-117">ISymUnmanagedWriter3 介面</span><span class="sxs-lookup"><span data-stu-id="583b6-117">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
