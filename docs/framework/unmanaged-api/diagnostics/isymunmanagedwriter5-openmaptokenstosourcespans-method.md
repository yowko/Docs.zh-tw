---
title: ISymUnmanagedWriter5::OpenMapTokensToSourceSpans 方法
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60c1984e6193481efdaaeb82a2bc025aef67a33f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534432"
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="41aa8-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans 方法</span><span class="sxs-lookup"><span data-stu-id="41aa8-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="41aa8-103">開啟要發出至來源語彙基元範圍的對應資訊的特殊的自訂資料 區段。</span><span class="sxs-lookup"><span data-stu-id="41aa8-103">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="41aa8-104">方法已開啟，或反之亦然，會發生錯誤時，請開啟這一節。</span><span class="sxs-lookup"><span data-stu-id="41aa8-104">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41aa8-105">語法</span><span class="sxs-lookup"><span data-stu-id="41aa8-105">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="41aa8-106">傳回值</span><span class="sxs-lookup"><span data-stu-id="41aa8-106">Return Value</span></span>  
 <span data-ttu-id="41aa8-107">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="41aa8-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41aa8-108">需求</span><span class="sxs-lookup"><span data-stu-id="41aa8-108">Requirements</span></span>  
 <span data-ttu-id="41aa8-109">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="41aa8-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41aa8-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41aa8-110">See also</span></span>
- [<span data-ttu-id="41aa8-111">ISymUnmanagedWriter5 介面</span><span class="sxs-lookup"><span data-stu-id="41aa8-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
