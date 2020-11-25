---
title: ISymUnmanagedWriter5 介面
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
ms.openlocfilehash: 894f3b0e45df2c681cbdec1f154703be64f32fc5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725790"
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="7a018-102">ISymUnmanagedWriter5 介面</span><span class="sxs-lookup"><span data-stu-id="7a018-102">ISymUnmanagedWriter5 Interface</span></span>

<span data-ttu-id="7a018-103">ISymUnmanagedWriter5 介面。</span><span class="sxs-lookup"><span data-stu-id="7a018-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a018-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="7a018-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="7a018-105">方法</span><span class="sxs-lookup"><span data-stu-id="7a018-105">Methods</span></span>  

 <span data-ttu-id="7a018-106">這個介面包含下列方法：</span><span class="sxs-lookup"><span data-stu-id="7a018-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="7a018-107">方法</span><span class="sxs-lookup"><span data-stu-id="7a018-107">Method</span></span>|<span data-ttu-id="7a018-108">描述</span><span class="sxs-lookup"><span data-stu-id="7a018-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7a018-109">CloseMapTokensToSourceSpans 方法</span><span class="sxs-lookup"><span data-stu-id="7a018-109">CloseMapTokensToSourceSpans Method</span></span>](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="7a018-110">針對權杖對來源範圍的對應資訊，關閉特殊的自訂資料區段。</span><span class="sxs-lookup"><span data-stu-id="7a018-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="7a018-111">關閉之後，就無法再加入任何對應資訊。</span><span class="sxs-lookup"><span data-stu-id="7a018-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="7a018-112">MapTokenToSourceSpan 方法</span><span class="sxs-lookup"><span data-stu-id="7a018-112">MapTokenToSourceSpan Method</span></span>](isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="7a018-113">將指定的元資料標記對應至指定原始程式檔中的指定原始程式列範圍。</span><span class="sxs-lookup"><span data-stu-id="7a018-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="7a018-114">必須在呼叫 [OpenMapTokensToSourceSpans 方法](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) 和 [CloseMapTokensToSourceSpans 方法](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)之間呼叫。</span><span class="sxs-lookup"><span data-stu-id="7a018-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="7a018-115">OpenMapTokensToSourceSpans 方法</span><span class="sxs-lookup"><span data-stu-id="7a018-115">OpenMapTokensToSourceSpans Method</span></span>](isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="7a018-116">開啟特殊的自訂資料區段，以在中發出權杖對來源範圍的對應資訊。</span><span class="sxs-lookup"><span data-stu-id="7a018-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="7a018-117">當方法已經開啟時開啟此區段，反之亦然，則是錯誤。</span><span class="sxs-lookup"><span data-stu-id="7a018-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7a018-118">需求</span><span class="sxs-lookup"><span data-stu-id="7a018-118">Requirements</span></span>  

 <span data-ttu-id="7a018-119">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="7a018-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a018-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a018-120">See also</span></span>

- [<span data-ttu-id="7a018-121">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="7a018-121">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="7a018-122">ISymUnmanagedWriter4 介面</span><span class="sxs-lookup"><span data-stu-id="7a018-122">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)
