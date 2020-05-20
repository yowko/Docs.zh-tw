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
ms.openlocfilehash: fdf24bb8533da7914128f9477987c427442383bb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610115"
---
# <a name="isymunmanagedwriterclosemethod-method"></a><span data-ttu-id="43d55-102">ISymUnmanagedWriter::CloseMethod 方法</span><span class="sxs-lookup"><span data-stu-id="43d55-102">ISymUnmanagedWriter::CloseMethod Method</span></span>
<span data-ttu-id="43d55-103">關閉目前的方法。</span><span class="sxs-lookup"><span data-stu-id="43d55-103">Closes the current method.</span></span> <span data-ttu-id="43d55-104">關閉方法後，就不能在其中定義更多符號。</span><span class="sxs-lookup"><span data-stu-id="43d55-104">Once a method is closed, no more symbols can be defined within it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43d55-105">語法</span><span class="sxs-lookup"><span data-stu-id="43d55-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseMethod();  
```  
  
## <a name="return-value"></a><span data-ttu-id="43d55-106">傳回值</span><span class="sxs-lookup"><span data-stu-id="43d55-106">Return Value</span></span>  
 <span data-ttu-id="43d55-107">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="43d55-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43d55-108">需求</span><span class="sxs-lookup"><span data-stu-id="43d55-108">Requirements</span></span>  
 <span data-ttu-id="43d55-109">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="43d55-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43d55-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43d55-110">See also</span></span>

- [<span data-ttu-id="43d55-111">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="43d55-111">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="43d55-112">OpenMethod 方法</span><span class="sxs-lookup"><span data-stu-id="43d55-112">OpenMethod Method</span></span>](isymunmanagedwriter-openmethod-method.md)
