---
title: ISymUnmanagedDocument::GetLanguage 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetLanguage
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetLanguage
helpviewer_keywords:
- ISymUnmanagedDocument::GetLanguage method [.NET Framework debugging]
- GetLanguage method [.NET Framework debugging]
ms.assetid: c6639418-e9f2-4a99-8ce2-ec9876e0bc79
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 05ce47953358b7025e30080fbbaf288a6c0e879d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939837"
---
# <a name="isymunmanageddocumentgetlanguage-method"></a><span data-ttu-id="828e7-102">ISymUnmanagedDocument::GetLanguage 方法</span><span class="sxs-lookup"><span data-stu-id="828e7-102">ISymUnmanagedDocument::GetLanguage Method</span></span>
<span data-ttu-id="828e7-103">取得這份文件的語言識別碼</span><span class="sxs-lookup"><span data-stu-id="828e7-103">Gets the language identifier of this document</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="828e7-104">語法</span><span class="sxs-lookup"><span data-stu-id="828e7-104">Syntax</span></span>  
  
```  
HRESULT GetLanguage(  
    [out, retval]  GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="828e7-105">參數</span><span class="sxs-lookup"><span data-stu-id="828e7-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="828e7-106">[out]接收的語言識別碼的變數指標。</span><span class="sxs-lookup"><span data-stu-id="828e7-106">[out] A pointer to a variable that receives the language identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="828e7-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="828e7-107">Return Value</span></span>  
 <span data-ttu-id="828e7-108">如果方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="828e7-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="828e7-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="828e7-109">See also</span></span>

- [<span data-ttu-id="828e7-110">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="828e7-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
