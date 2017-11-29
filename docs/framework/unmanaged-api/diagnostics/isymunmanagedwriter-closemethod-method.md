---
title: "ISymUnmanagedWriter::CloseMethod 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.CloseMethod
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::CloseMethod
helpviewer_keywords:
- ISymUnmanagedWriter::CloseMethod method [.NET Framework debugging]
- CloseMethod method [.NET Framework debugging]
ms.assetid: b8025e04-f0e5-40c8-849c-8cd51323420e
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ea4f917a5e553eb2541f20ce08d403adc7d86d44
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriterclosemethod-method"></a><span data-ttu-id="330b7-102">ISymUnmanagedWriter::CloseMethod 方法</span><span class="sxs-lookup"><span data-stu-id="330b7-102">ISymUnmanagedWriter::CloseMethod Method</span></span>
<span data-ttu-id="330b7-103">關閉目前的方法。</span><span class="sxs-lookup"><span data-stu-id="330b7-103">Closes the current method.</span></span> <span data-ttu-id="330b7-104">一旦關閉方法，可以不定義任何符號，於其中。</span><span class="sxs-lookup"><span data-stu-id="330b7-104">Once a method is closed, no more symbols can be defined within it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="330b7-105">語法</span><span class="sxs-lookup"><span data-stu-id="330b7-105">Syntax</span></span>  
  
```  
HRESULT CloseMethod();  
```  
  
## <a name="return-value"></a><span data-ttu-id="330b7-106">傳回值</span><span class="sxs-lookup"><span data-stu-id="330b7-106">Return Value</span></span>  
 <span data-ttu-id="330b7-107">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="330b7-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="330b7-108">需求</span><span class="sxs-lookup"><span data-stu-id="330b7-108">Requirements</span></span>  
 <span data-ttu-id="330b7-109">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="330b7-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="330b7-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="330b7-110">See Also</span></span>  
 [<span data-ttu-id="330b7-111">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="330b7-111">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="330b7-112">OpenMethod 方法</span><span class="sxs-lookup"><span data-stu-id="330b7-112">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
