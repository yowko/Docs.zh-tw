---
title: "ISymUnmanagedWriter5::OpenMapTokensToSourceSpans 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f226a71ac6381c8ca04093beb1d9772d6e6c75e3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="81f19-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans 方法</span><span class="sxs-lookup"><span data-stu-id="81f19-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="81f19-103">開啟發出到語彙基元至來源範圍的對應資訊的特殊的自訂資料區段。</span><span class="sxs-lookup"><span data-stu-id="81f19-103">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="81f19-104">方法已經開啟，或反之亦然，會發生錯誤時，請開啟此區段。</span><span class="sxs-lookup"><span data-stu-id="81f19-104">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81f19-105">語法</span><span class="sxs-lookup"><span data-stu-id="81f19-105">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="81f19-106">傳回值</span><span class="sxs-lookup"><span data-stu-id="81f19-106">Return Value</span></span>  
 <span data-ttu-id="81f19-107">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="81f19-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81f19-108">需求</span><span class="sxs-lookup"><span data-stu-id="81f19-108">Requirements</span></span>  
 <span data-ttu-id="81f19-109">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="81f19-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81f19-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81f19-110">See Also</span></span>  
 [<span data-ttu-id="81f19-111">ISymUnmanagedWriter5 介面</span><span class="sxs-lookup"><span data-stu-id="81f19-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
