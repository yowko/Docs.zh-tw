---
title: ISymUnmanagedWriter3 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3
helpviewer_keywords:
- ISymUnmanagedWriter3 interface [.NET Framework debugging]
ms.assetid: a034c21e-e371-4360-b470-29e88288948f
topic_type:
- apiref
ms.openlocfilehash: 006045ce101884119f676e4f6324815eb21a10a4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614652"
---
# <a name="isymunmanagedwriter3-interface"></a><span data-ttu-id="ebc94-102">ISymUnmanagedWriter3 介面</span><span class="sxs-lookup"><span data-stu-id="ebc94-102">ISymUnmanagedWriter3 Interface</span></span>
<span data-ttu-id="ebc94-103">表示符號寫入器，並提供定義檔、序列點、詞法範圍和變數的方法。</span><span class="sxs-lookup"><span data-stu-id="ebc94-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="ebc94-104">這個介面會擴充[ISymUnmanagedWriter](isymunmanagedwriter-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="ebc94-104">This interface extends the [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ebc94-105">方法</span><span class="sxs-lookup"><span data-stu-id="ebc94-105">Methods</span></span>  
  
|<span data-ttu-id="ebc94-106">方法</span><span class="sxs-lookup"><span data-stu-id="ebc94-106">Method</span></span>|<span data-ttu-id="ebc94-107">描述</span><span class="sxs-lookup"><span data-stu-id="ebc94-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ebc94-108">Commit 方法</span><span class="sxs-lookup"><span data-stu-id="ebc94-108">Commit Method</span></span>](isymunmanagedwriter3-commit-method.md)|<span data-ttu-id="ebc94-109">認可到目前為止寫入資料流程的變更。</span><span class="sxs-lookup"><span data-stu-id="ebc94-109">Commits the changes written so far to the stream.</span></span>|  
|[<span data-ttu-id="ebc94-110">OpenMethod2 方法</span><span class="sxs-lookup"><span data-stu-id="ebc94-110">OpenMethod2 Method</span></span>](isymunmanagedwriter3-openmethod2-method.md)|<span data-ttu-id="ebc94-111">開啟方法，並在影像中提供其實數區段位移。</span><span class="sxs-lookup"><span data-stu-id="ebc94-111">Opens a method and provides its real section offset in the image.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ebc94-112">需求</span><span class="sxs-lookup"><span data-stu-id="ebc94-112">Requirements</span></span>  
 <span data-ttu-id="ebc94-113">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="ebc94-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebc94-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ebc94-114">See also</span></span>

- [<span data-ttu-id="ebc94-115">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="ebc94-115">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="ebc94-116">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="ebc94-116">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="ebc94-117">ISymUnmanagedWriter2 介面</span><span class="sxs-lookup"><span data-stu-id="ebc94-117">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
