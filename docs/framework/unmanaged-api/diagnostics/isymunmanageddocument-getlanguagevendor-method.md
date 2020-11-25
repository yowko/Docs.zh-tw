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
ms.openlocfilehash: bac0f187409a191dda1ef635ec9b2da1aee25981
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700947"
---
# <a name="isymunmanageddocumentgetlanguagevendor-method"></a><span data-ttu-id="52cf8-102">ISymUnmanagedDocument::GetLanguageVendor 方法</span><span class="sxs-lookup"><span data-stu-id="52cf8-102">ISymUnmanagedDocument::GetLanguageVendor Method</span></span>

<span data-ttu-id="52cf8-103">取得此檔的語言廠商。</span><span class="sxs-lookup"><span data-stu-id="52cf8-103">Gets the language vendor of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52cf8-104">語法</span><span class="sxs-lookup"><span data-stu-id="52cf8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLanguageVendor(  
    [out, retval]  GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52cf8-105">參數</span><span class="sxs-lookup"><span data-stu-id="52cf8-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="52cf8-106">擴展接收語言廠商之變數的指標。</span><span class="sxs-lookup"><span data-stu-id="52cf8-106">[out] A pointer to a variable that receives the language vendor.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52cf8-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="52cf8-107">Return Value</span></span>  

 <span data-ttu-id="52cf8-108">如果方法成功，則為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="52cf8-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52cf8-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52cf8-109">See also</span></span>

- [<span data-ttu-id="52cf8-110">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="52cf8-110">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
