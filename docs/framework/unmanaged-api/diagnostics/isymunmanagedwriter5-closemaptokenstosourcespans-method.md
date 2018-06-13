---
title: ISymUnmanagedWriter5::CloseMapTokensToSourceSpans 方法
ms.date: 03/30/2017
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 653dd933066898c1954cfbcc57c0c0493e47b4be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428608"
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="de62c-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans 方法</span><span class="sxs-lookup"><span data-stu-id="de62c-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="de62c-103">關閉對應資訊的語彙基元至來源範圍的特殊的自訂資料區段。</span><span class="sxs-lookup"><span data-stu-id="de62c-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="de62c-104">它已關閉之後，就可以加入沒有對應的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="de62c-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de62c-105">語法</span><span class="sxs-lookup"><span data-stu-id="de62c-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="de62c-106">傳回值</span><span class="sxs-lookup"><span data-stu-id="de62c-106">Return Value</span></span>  
 <span data-ttu-id="de62c-107">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="de62c-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de62c-108">需求</span><span class="sxs-lookup"><span data-stu-id="de62c-108">Requirements</span></span>  
 <span data-ttu-id="de62c-109">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="de62c-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de62c-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de62c-110">See Also</span></span>  
 [<span data-ttu-id="de62c-111">ISymUnmanagedWriter5 介面</span><span class="sxs-lookup"><span data-stu-id="de62c-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
