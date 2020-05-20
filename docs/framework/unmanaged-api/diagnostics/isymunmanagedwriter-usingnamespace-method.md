---
title: ISymUnmanagedWriter::UsingNamespace 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.UsingNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::UsingNamespace
helpviewer_keywords:
- UsingNamespace method [.NET Framework debugging]
- ISymUnmanagedWriter::UsingNamespace method [.NET Framework debugging]
ms.assetid: 8d746e0a-d158-4983-88da-db0a0856bc0b
topic_type:
- apiref
ms.openlocfilehash: e4348cc59924b65b6c6bb53a9c2a98f1a1161b50
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614730"
---
# <a name="isymunmanagedwriterusingnamespace-method"></a><span data-ttu-id="cec6b-102">ISymUnmanagedWriter::UsingNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="cec6b-102">ISymUnmanagedWriter::UsingNamespace Method</span></span>
<span data-ttu-id="cec6b-103">指定在目前開啟的詞法範圍內使用指定的完整命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="cec6b-103">Specifies that the given fully qualified namespace name is being used within the currently open lexical scope.</span></span> <span data-ttu-id="cec6b-104">命名空間將會用於繼承自目前開啟範圍的所有範圍內。</span><span class="sxs-lookup"><span data-stu-id="cec6b-104">The namespace will be used within all scopes that inherit from the currently open scope.</span></span> <span data-ttu-id="cec6b-105">關閉目前的範圍也會停止使用命名空間。</span><span class="sxs-lookup"><span data-stu-id="cec6b-105">Closing the current scope will also stop the use of the namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cec6b-106">語法</span><span class="sxs-lookup"><span data-stu-id="cec6b-106">Syntax</span></span>  
  
```cpp  
HRESULT UsingNamespace(  
    [in] const WCHAR *fullName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cec6b-107">參數</span><span class="sxs-lookup"><span data-stu-id="cec6b-107">Parameters</span></span>  
 `fullName`  
 <span data-ttu-id="cec6b-108">在命名空間之完整名稱的指標。</span><span class="sxs-lookup"><span data-stu-id="cec6b-108">[in] A pointer to the fully qualified name of the namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cec6b-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="cec6b-109">Return Value</span></span>  
 <span data-ttu-id="cec6b-110">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="cec6b-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cec6b-111">需求</span><span class="sxs-lookup"><span data-stu-id="cec6b-111">Requirements</span></span>  
 <span data-ttu-id="cec6b-112">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="cec6b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cec6b-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cec6b-113">See also</span></span>

- [<span data-ttu-id="cec6b-114">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="cec6b-114">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
