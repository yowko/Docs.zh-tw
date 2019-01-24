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
ms.openlocfilehash: b73c9d6fa802a90e59345eb477bccfe80cf2275e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704926"
---
# <a name="isymunmanageddocumentgetlanguagevendor-method"></a><span data-ttu-id="04407-102">ISymUnmanagedDocument::GetLanguageVendor 方法</span><span class="sxs-lookup"><span data-stu-id="04407-102">ISymUnmanagedDocument::GetLanguageVendor Method</span></span>
<span data-ttu-id="04407-103">取得這份文件的語言廠商。</span><span class="sxs-lookup"><span data-stu-id="04407-103">Gets the language vendor of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04407-104">語法</span><span class="sxs-lookup"><span data-stu-id="04407-104">Syntax</span></span>  
  
```  
HRESULT GetLanguageVendor(  
    [out, retval]  GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="04407-105">參數</span><span class="sxs-lookup"><span data-stu-id="04407-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="04407-106">[out]接收的語言廠商的變數指標。</span><span class="sxs-lookup"><span data-stu-id="04407-106">[out] A pointer to a variable that receives the language vendor.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04407-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="04407-107">Return Value</span></span>  
 <span data-ttu-id="04407-108">如果方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="04407-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04407-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04407-109">See also</span></span>
- [<span data-ttu-id="04407-110">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="04407-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
