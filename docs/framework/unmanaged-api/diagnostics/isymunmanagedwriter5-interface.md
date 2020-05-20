---
title: ISymUnmanagedWriter5 介面
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
ms.openlocfilehash: bdc630c3c94c7d03b736efa0a95665f10aac7c6e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609426"
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="f80cc-102">ISymUnmanagedWriter5 介面</span><span class="sxs-lookup"><span data-stu-id="f80cc-102">ISymUnmanagedWriter5 Interface</span></span>
<span data-ttu-id="f80cc-103">ISymUnmanagedWriter5 介面。</span><span class="sxs-lookup"><span data-stu-id="f80cc-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f80cc-104">語法</span><span class="sxs-lookup"><span data-stu-id="f80cc-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="f80cc-105">方法</span><span class="sxs-lookup"><span data-stu-id="f80cc-105">Methods</span></span>  
 <span data-ttu-id="f80cc-106">這個介面包含下列方法：</span><span class="sxs-lookup"><span data-stu-id="f80cc-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="f80cc-107">方法</span><span class="sxs-lookup"><span data-stu-id="f80cc-107">Method</span></span>|<span data-ttu-id="f80cc-108">描述</span><span class="sxs-lookup"><span data-stu-id="f80cc-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f80cc-109">CloseMapTokensToSourceSpans 方法</span><span class="sxs-lookup"><span data-stu-id="f80cc-109">CloseMapTokensToSourceSpans Method</span></span>](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="f80cc-110">關閉 [特殊自訂資料] 區段，以取得權杖對來源的對應資訊。</span><span class="sxs-lookup"><span data-stu-id="f80cc-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="f80cc-111">關閉之後，就無法再新增任何對應資訊。</span><span class="sxs-lookup"><span data-stu-id="f80cc-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="f80cc-112">MapTokenToSourceSpan 方法</span><span class="sxs-lookup"><span data-stu-id="f80cc-112">MapTokenToSourceSpan Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="f80cc-113">將給定的元資料標記對應至指定之原始程式檔中的給定原始程式列範圍。</span><span class="sxs-lookup"><span data-stu-id="f80cc-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="f80cc-114">必須在[OpenMapTokensToSourceSpans 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)和[CloseMapTokensToSourceSpans 方法](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)的呼叫之間呼叫。</span><span class="sxs-lookup"><span data-stu-id="f80cc-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="f80cc-115">OpenMapTokensToSourceSpans 方法</span><span class="sxs-lookup"><span data-stu-id="f80cc-115">OpenMapTokensToSourceSpans Method</span></span>](isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="f80cc-116">開啟特殊的自訂資料區段，以在中發出權杖對來源的範圍對應資訊。</span><span class="sxs-lookup"><span data-stu-id="f80cc-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="f80cc-117">當方法已經開啟時開啟此區段，反之亦然，則為錯誤。</span><span class="sxs-lookup"><span data-stu-id="f80cc-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f80cc-118">需求</span><span class="sxs-lookup"><span data-stu-id="f80cc-118">Requirements</span></span>  
 <span data-ttu-id="f80cc-119">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="f80cc-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f80cc-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f80cc-120">See also</span></span>

- [<span data-ttu-id="f80cc-121">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="f80cc-121">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="f80cc-122">ISymUnmanagedWriter4 介面</span><span class="sxs-lookup"><span data-stu-id="f80cc-122">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)
