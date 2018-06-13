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
ms.openlocfilehash: 98c981a10a07d035300349cc8687b3201ed70927
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424293"
---
# <a name="isymunmanageddocumentgetlanguage-method"></a><span data-ttu-id="a39a9-102">ISymUnmanagedDocument::GetLanguage 方法</span><span class="sxs-lookup"><span data-stu-id="a39a9-102">ISymUnmanagedDocument::GetLanguage Method</span></span>
<span data-ttu-id="a39a9-103">取得這份文件的語言識別項</span><span class="sxs-lookup"><span data-stu-id="a39a9-103">Gets the language identifier of this document</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a39a9-104">語法</span><span class="sxs-lookup"><span data-stu-id="a39a9-104">Syntax</span></span>  
  
```  
HRESULT GetLanguage(  
    [out, retval]  GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a39a9-105">參數</span><span class="sxs-lookup"><span data-stu-id="a39a9-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="a39a9-106">[out]此變數會接收的語言識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="a39a9-106">[out] A pointer to a variable that receives the language identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a39a9-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="a39a9-107">Return Value</span></span>  
 <span data-ttu-id="a39a9-108">如果此方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="a39a9-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a39a9-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a39a9-109">See Also</span></span>  
 [<span data-ttu-id="a39a9-110">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="a39a9-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
