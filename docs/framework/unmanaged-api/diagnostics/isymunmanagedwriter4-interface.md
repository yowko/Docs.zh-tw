---
title: ISymUnmanagedWriter4 介面
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a5e44541a18f10588e899f59a166406c149691f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54650043"
---
# <a name="isymunmanagedwriter4-interface"></a><span data-ttu-id="349bf-102">ISymUnmanagedWriter4 介面</span><span class="sxs-lookup"><span data-stu-id="349bf-102">ISymUnmanagedWriter4 Interface</span></span>
<span data-ttu-id="349bf-103">ISymUnmanagedWriter4 介面。</span><span class="sxs-lookup"><span data-stu-id="349bf-103">ISymUnmanagedWriter4 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="349bf-104">語法</span><span class="sxs-lookup"><span data-stu-id="349bf-104">Syntax</span></span>  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a><span data-ttu-id="349bf-105">方法</span><span class="sxs-lookup"><span data-stu-id="349bf-105">Methods</span></span>  
 <span data-ttu-id="349bf-106">這個介面包含下列方法：</span><span class="sxs-lookup"><span data-stu-id="349bf-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="349bf-107">方法</span><span class="sxs-lookup"><span data-stu-id="349bf-107">Method</span></span>|<span data-ttu-id="349bf-108">描述</span><span class="sxs-lookup"><span data-stu-id="349bf-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="349bf-109">GetDebugInfoWithPadding 方法</span><span class="sxs-lookup"><span data-stu-id="349bf-109">GetDebugInfoWithPadding Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|<span data-ttu-id="349bf-110">函數一樣[GetDebugInfo 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md)不同之處在於路徑字串以下列結束的 null 字元，讓字串資料的固定的大小的零來填補`MAX_PATH`。</span><span class="sxs-lookup"><span data-stu-id="349bf-110">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="349bf-111">如果路徑字串的長度本身是只指定填補小於`MAX_PATH`。</span><span class="sxs-lookup"><span data-stu-id="349bf-111">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span><br /><br /> <span data-ttu-id="349bf-112">這可讓您更輕鬆地撰寫工具類型的差異 PE 檔案。</span><span class="sxs-lookup"><span data-stu-id="349bf-112">This makes it easier to write tools that difference PE files.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="349bf-113">需求</span><span class="sxs-lookup"><span data-stu-id="349bf-113">Requirements</span></span>  
 <span data-ttu-id="349bf-114">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="349bf-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="349bf-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="349bf-115">See also</span></span>
- [<span data-ttu-id="349bf-116">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="349bf-116">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="349bf-117">ISymUnmanagedWriter3 介面</span><span class="sxs-lookup"><span data-stu-id="349bf-117">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
