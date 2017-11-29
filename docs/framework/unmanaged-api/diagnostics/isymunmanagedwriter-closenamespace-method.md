---
title: "ISymUnmanagedWriter::CloseNamespace 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.CloseNamespace
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::CloseNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::CloseNamespace method [.NET Framework debugging]
- CloseNamespace method [.NET Framework debugging]
ms.assetid: 7f74d9c5-1377-4958-b842-6306d611cbd5
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8423e21fbc868e4b6891279d19b2be7c1faef583
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriterclosenamespace-method"></a><span data-ttu-id="684d3-102">ISymUnmanagedWriter::CloseNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="684d3-102">ISymUnmanagedWriter::CloseNamespace Method</span></span>
<span data-ttu-id="684d3-103">關閉最近開啟的命名空間。</span><span class="sxs-lookup"><span data-stu-id="684d3-103">Closes the most recently opened namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="684d3-104">語法</span><span class="sxs-lookup"><span data-stu-id="684d3-104">Syntax</span></span>  
  
```  
HRESULT CloseNamespace();  
```  
  
## <a name="return-value"></a><span data-ttu-id="684d3-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="684d3-105">Return Value</span></span>  
 <span data-ttu-id="684d3-106">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="684d3-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="684d3-107">需求</span><span class="sxs-lookup"><span data-stu-id="684d3-107">Requirements</span></span>  
 <span data-ttu-id="684d3-108">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="684d3-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="684d3-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="684d3-109">See Also</span></span>  
 [<span data-ttu-id="684d3-110">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="684d3-110">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="684d3-111">OpenNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="684d3-111">OpenNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)
