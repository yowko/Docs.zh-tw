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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9a5ff52a95fd6ebaec05439cbc702d5513d0cc78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427765"
---
# <a name="isymunmanagedwriterusingnamespace-method"></a><span data-ttu-id="ca936-102">ISymUnmanagedWriter::UsingNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="ca936-102">ISymUnmanagedWriter::UsingNamespace Method</span></span>
<span data-ttu-id="ca936-103">指定確認目前開啟的語彙範圍內使用指定的完整命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="ca936-103">Specifies that the given fully qualified namespace name is being used within the currently open lexical scope.</span></span> <span data-ttu-id="ca936-104">命名空間將用於所有領域都繼承自目前開啟的範圍內。</span><span class="sxs-lookup"><span data-stu-id="ca936-104">The namespace will be used within all scopes that inherit from the currently open scope.</span></span> <span data-ttu-id="ca936-105">關閉目前的範圍也會停止使用命名空間。</span><span class="sxs-lookup"><span data-stu-id="ca936-105">Closing the current scope will also stop the use of the namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca936-106">語法</span><span class="sxs-lookup"><span data-stu-id="ca936-106">Syntax</span></span>  
  
```  
HRESULT UsingNamespace(  
    [in] const WCHAR *fullName);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ca936-107">參數</span><span class="sxs-lookup"><span data-stu-id="ca936-107">Parameters</span></span>  
 `fullName`  
 <span data-ttu-id="ca936-108">[in]命名空間的完整名稱指標。</span><span class="sxs-lookup"><span data-stu-id="ca936-108">[in] A pointer to the fully qualified name of the namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca936-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="ca936-109">Return Value</span></span>  
 <span data-ttu-id="ca936-110">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="ca936-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca936-111">需求</span><span class="sxs-lookup"><span data-stu-id="ca936-111">Requirements</span></span>  
 <span data-ttu-id="ca936-112">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ca936-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca936-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca936-113">See Also</span></span>  
 [<span data-ttu-id="ca936-114">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="ca936-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
