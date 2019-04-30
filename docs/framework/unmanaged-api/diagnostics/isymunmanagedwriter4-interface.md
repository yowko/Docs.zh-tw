---
title: ISymUnmanagedWriter4 介面
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5732cc08512df25a14cc8ea9dcaa03c56207dde
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61962327"
---
# <a name="isymunmanagedwriter4-interface"></a><span data-ttu-id="5378e-102">ISymUnmanagedWriter4 介面</span><span class="sxs-lookup"><span data-stu-id="5378e-102">ISymUnmanagedWriter4 Interface</span></span>
<span data-ttu-id="5378e-103">ISymUnmanagedWriter4 介面。</span><span class="sxs-lookup"><span data-stu-id="5378e-103">ISymUnmanagedWriter4 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5378e-104">語法</span><span class="sxs-lookup"><span data-stu-id="5378e-104">Syntax</span></span>  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a><span data-ttu-id="5378e-105">方法</span><span class="sxs-lookup"><span data-stu-id="5378e-105">Methods</span></span>  
 <span data-ttu-id="5378e-106">這個介面包含下列方法：</span><span class="sxs-lookup"><span data-stu-id="5378e-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="5378e-107">方法</span><span class="sxs-lookup"><span data-stu-id="5378e-107">Method</span></span>|<span data-ttu-id="5378e-108">描述</span><span class="sxs-lookup"><span data-stu-id="5378e-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5378e-109">GetDebugInfoWithPadding 方法</span><span class="sxs-lookup"><span data-stu-id="5378e-109">GetDebugInfoWithPadding Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|<span data-ttu-id="5378e-110">函數一樣[GetDebugInfo 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md)不同之處在於路徑字串以下列結束的 null 字元，讓字串資料的固定的大小的零來填補`MAX_PATH`。</span><span class="sxs-lookup"><span data-stu-id="5378e-110">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="5378e-111">如果路徑字串的長度本身是只指定填補小於`MAX_PATH`。</span><span class="sxs-lookup"><span data-stu-id="5378e-111">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span><br /><br /> <span data-ttu-id="5378e-112">這可讓您更輕鬆地撰寫工具類型的差異 PE 檔案。</span><span class="sxs-lookup"><span data-stu-id="5378e-112">This makes it easier to write tools that difference PE files.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5378e-113">需求</span><span class="sxs-lookup"><span data-stu-id="5378e-113">Requirements</span></span>  
 <span data-ttu-id="5378e-114">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5378e-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5378e-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5378e-115">See also</span></span>

- [<span data-ttu-id="5378e-116">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="5378e-116">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="5378e-117">ISymUnmanagedWriter3 介面</span><span class="sxs-lookup"><span data-stu-id="5378e-117">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
