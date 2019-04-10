---
title: ISymUnmanagedWriter5::OpenMapTokensToSourceSpans 方法
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82dc2ced988f7277c994eb9449e7c26efa5450b7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222675"
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="10387-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans 方法</span><span class="sxs-lookup"><span data-stu-id="10387-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="10387-103">開啟要發出至來源語彙基元範圍的對應資訊的特殊的自訂資料 區段。</span><span class="sxs-lookup"><span data-stu-id="10387-103">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="10387-104">方法已開啟，或反之亦然，會發生錯誤時，請開啟這一節。</span><span class="sxs-lookup"><span data-stu-id="10387-104">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10387-105">語法</span><span class="sxs-lookup"><span data-stu-id="10387-105">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="10387-106">傳回值</span><span class="sxs-lookup"><span data-stu-id="10387-106">Return Value</span></span>  
 <span data-ttu-id="10387-107">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="10387-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10387-108">需求</span><span class="sxs-lookup"><span data-stu-id="10387-108">Requirements</span></span>  
 <span data-ttu-id="10387-109">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="10387-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10387-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10387-110">See also</span></span>

- [<span data-ttu-id="10387-111">ISymUnmanagedWriter5 介面</span><span class="sxs-lookup"><span data-stu-id="10387-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
