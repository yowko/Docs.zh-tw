---
title: ISymUnmanagedDocument::GetLanguageVendor 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetLanguageVendor
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetLanguageVendor
helpviewer_keywords:
- GetLanguageVendor method [.NET Framework debugging]
- ISymUnmanagedDocument::GetLanguageVendor method [.NET Framework debugging]
ms.assetid: 1d4b702e-4922-441d-8b44-03804284f70b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f5140462ae3c869d58187351d2e0ff11f7b6e179
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776686"
---
# <a name="isymunmanageddocumentgetlanguagevendor-method"></a><span data-ttu-id="2e724-102">ISymUnmanagedDocument::GetLanguageVendor 方法</span><span class="sxs-lookup"><span data-stu-id="2e724-102">ISymUnmanagedDocument::GetLanguageVendor Method</span></span>
<span data-ttu-id="2e724-103">取得這份文件的語言廠商。</span><span class="sxs-lookup"><span data-stu-id="2e724-103">Gets the language vendor of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e724-104">語法</span><span class="sxs-lookup"><span data-stu-id="2e724-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLanguageVendor(  
    [out, retval]  GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e724-105">參數</span><span class="sxs-lookup"><span data-stu-id="2e724-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="2e724-106">[out]接收的語言廠商的變數指標。</span><span class="sxs-lookup"><span data-stu-id="2e724-106">[out] A pointer to a variable that receives the language vendor.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2e724-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="2e724-107">Return Value</span></span>  
 <span data-ttu-id="2e724-108">如果方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="2e724-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e724-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e724-109">See also</span></span>

- [<span data-ttu-id="2e724-110">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="2e724-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
