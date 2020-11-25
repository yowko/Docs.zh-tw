---
title: ISymUnmanagedWriter4 介面
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
ms.openlocfilehash: c2b57897e4f0e8b23337302f344065d79677e0c4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725803"
---
# <a name="isymunmanagedwriter4-interface"></a><span data-ttu-id="3bbff-102">ISymUnmanagedWriter4 介面</span><span class="sxs-lookup"><span data-stu-id="3bbff-102">ISymUnmanagedWriter4 Interface</span></span>

<span data-ttu-id="3bbff-103">ISymUnmanagedWriter4 介面。</span><span class="sxs-lookup"><span data-stu-id="3bbff-103">ISymUnmanagedWriter4 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bbff-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="3bbff-104">Syntax</span></span>  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a><span data-ttu-id="3bbff-105">方法</span><span class="sxs-lookup"><span data-stu-id="3bbff-105">Methods</span></span>  

 <span data-ttu-id="3bbff-106">這個介面包含下列方法：</span><span class="sxs-lookup"><span data-stu-id="3bbff-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="3bbff-107">方法</span><span class="sxs-lookup"><span data-stu-id="3bbff-107">Method</span></span>|<span data-ttu-id="3bbff-108">描述</span><span class="sxs-lookup"><span data-stu-id="3bbff-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3bbff-109">GetDebugInfoWithPadding 方法</span><span class="sxs-lookup"><span data-stu-id="3bbff-109">GetDebugInfoWithPadding Method</span></span>](isymunmanagedwriter4-getdebuginfowithpadding-method.md)|<span data-ttu-id="3bbff-110">函式與 [GetDebugInfo 方法](isymunmanagedwriter-getdebuginfo-method.md) 相同，不同之處在于路徑字串在結束的 null 字元之後會以零填補，以使字串資料成為固定的大小 `MAX_PATH` 。</span><span class="sxs-lookup"><span data-stu-id="3bbff-110">Functions the same as [GetDebugInfo Method](isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="3bbff-111">只有當路徑字串長度本身小於時，才會提供填補 `MAX_PATH` 。</span><span class="sxs-lookup"><span data-stu-id="3bbff-111">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span><br /><br /> <span data-ttu-id="3bbff-112">這可讓您更輕鬆地撰寫與 PE 檔案不同的工具。</span><span class="sxs-lookup"><span data-stu-id="3bbff-112">This makes it easier to write tools that difference PE files.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3bbff-113">需求</span><span class="sxs-lookup"><span data-stu-id="3bbff-113">Requirements</span></span>  

 <span data-ttu-id="3bbff-114">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="3bbff-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bbff-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3bbff-115">See also</span></span>

- [<span data-ttu-id="3bbff-116">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="3bbff-116">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="3bbff-117">ISymUnmanagedWriter3 介面</span><span class="sxs-lookup"><span data-stu-id="3bbff-117">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
