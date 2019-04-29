---
title: ISymUnmanagedWriter::CloseMethod 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseMethod
helpviewer_keywords:
- ISymUnmanagedWriter::CloseMethod method [.NET Framework debugging]
- CloseMethod method [.NET Framework debugging]
ms.assetid: b8025e04-f0e5-40c8-849c-8cd51323420e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 591279a80b7d6a770127fb98eb71c056c48bdffd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934143"
---
# <a name="isymunmanagedwriterclosemethod-method"></a><span data-ttu-id="97852-102">ISymUnmanagedWriter::CloseMethod 方法</span><span class="sxs-lookup"><span data-stu-id="97852-102">ISymUnmanagedWriter::CloseMethod Method</span></span>
<span data-ttu-id="97852-103">關閉目前的方法。</span><span class="sxs-lookup"><span data-stu-id="97852-103">Closes the current method.</span></span> <span data-ttu-id="97852-104">一旦關閉方法，則可以在其中定義沒有更多的符號。</span><span class="sxs-lookup"><span data-stu-id="97852-104">Once a method is closed, no more symbols can be defined within it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97852-105">語法</span><span class="sxs-lookup"><span data-stu-id="97852-105">Syntax</span></span>  
  
```  
HRESULT CloseMethod();  
```  
  
## <a name="return-value"></a><span data-ttu-id="97852-106">傳回值</span><span class="sxs-lookup"><span data-stu-id="97852-106">Return Value</span></span>  
 <span data-ttu-id="97852-107">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="97852-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97852-108">需求</span><span class="sxs-lookup"><span data-stu-id="97852-108">Requirements</span></span>  
 <span data-ttu-id="97852-109">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="97852-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97852-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97852-110">See also</span></span>

- [<span data-ttu-id="97852-111">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="97852-111">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="97852-112">OpenMethod 方法</span><span class="sxs-lookup"><span data-stu-id="97852-112">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
