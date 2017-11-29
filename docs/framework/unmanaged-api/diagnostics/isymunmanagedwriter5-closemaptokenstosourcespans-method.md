---
title: "ISymUnmanagedWriter5::CloseMapTokensToSourceSpans 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f5f23c3fe39adcebcfdfadb9e9c2b639f16330d1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="b4f31-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans 方法</span><span class="sxs-lookup"><span data-stu-id="b4f31-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="b4f31-103">關閉對應資訊的語彙基元至來源範圍的特殊的自訂資料區段。</span><span class="sxs-lookup"><span data-stu-id="b4f31-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="b4f31-104">它已關閉之後，就可以加入沒有對應的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="b4f31-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4f31-105">語法</span><span class="sxs-lookup"><span data-stu-id="b4f31-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="b4f31-106">傳回值</span><span class="sxs-lookup"><span data-stu-id="b4f31-106">Return Value</span></span>  
 <span data-ttu-id="b4f31-107">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="b4f31-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4f31-108">需求</span><span class="sxs-lookup"><span data-stu-id="b4f31-108">Requirements</span></span>  
 <span data-ttu-id="b4f31-109">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b4f31-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4f31-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4f31-110">See Also</span></span>  
 [<span data-ttu-id="b4f31-111">ISymUnmanagedWriter5 介面</span><span class="sxs-lookup"><span data-stu-id="b4f31-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
