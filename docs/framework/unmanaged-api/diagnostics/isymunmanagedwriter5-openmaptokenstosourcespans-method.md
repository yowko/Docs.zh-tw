---
title: ISymUnmanagedWriter5::OpenMapTokensToSourceSpans 方法
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
ms.openlocfilehash: 82b46ea315009b65254735d44e355154b83b22e2
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609491"
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="b7fc7-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans 方法</span><span class="sxs-lookup"><span data-stu-id="b7fc7-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="b7fc7-103">開啟特殊的自訂資料區段，以在中發出權杖對來源的範圍對應資訊。</span><span class="sxs-lookup"><span data-stu-id="b7fc7-103">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="b7fc7-104">當方法已經開啟時開啟此區段，反之亦然，則為錯誤。</span><span class="sxs-lookup"><span data-stu-id="b7fc7-104">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7fc7-105">語法</span><span class="sxs-lookup"><span data-stu-id="b7fc7-105">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="b7fc7-106">傳回值</span><span class="sxs-lookup"><span data-stu-id="b7fc7-106">Return Value</span></span>  
 <span data-ttu-id="b7fc7-107">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="b7fc7-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7fc7-108">需求</span><span class="sxs-lookup"><span data-stu-id="b7fc7-108">Requirements</span></span>  
 <span data-ttu-id="b7fc7-109">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="b7fc7-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7fc7-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7fc7-110">See also</span></span>

- [<span data-ttu-id="b7fc7-111">ISymUnmanagedWriter5 介面</span><span class="sxs-lookup"><span data-stu-id="b7fc7-111">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
