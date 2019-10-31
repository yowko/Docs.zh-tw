---
title: ISymUnmanagedWriter5::OpenMapTokensToSourceSpans 方法
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
ms.openlocfilehash: 004e1ddae8a6c0262846422a2eeb4314a4c82f65
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121618"
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="5d42a-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans 方法</span><span class="sxs-lookup"><span data-stu-id="5d42a-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="5d42a-103">開啟特殊的自訂資料區段，以在中發出權杖對來源的範圍對應資訊。</span><span class="sxs-lookup"><span data-stu-id="5d42a-103">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="5d42a-104">當方法已經開啟時開啟此區段，反之亦然，則為錯誤。</span><span class="sxs-lookup"><span data-stu-id="5d42a-104">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d42a-105">語法</span><span class="sxs-lookup"><span data-stu-id="5d42a-105">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="5d42a-106">傳回值</span><span class="sxs-lookup"><span data-stu-id="5d42a-106">Return Value</span></span>  
 <span data-ttu-id="5d42a-107">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="5d42a-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d42a-108">需求</span><span class="sxs-lookup"><span data-stu-id="5d42a-108">Requirements</span></span>  
 <span data-ttu-id="5d42a-109">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="5d42a-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d42a-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="5d42a-110">See also</span></span>

- [<span data-ttu-id="5d42a-111">ISymUnmanagedWriter5 介面</span><span class="sxs-lookup"><span data-stu-id="5d42a-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
