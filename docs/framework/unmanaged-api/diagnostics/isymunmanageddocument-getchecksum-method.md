---
title: "ISymUnmanagedDocument::GetCheckSum 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.GetCheckSum
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::GetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSum method [.NET Framework debugging]
- GetCheckSum method [.NET Framework debugging]
ms.assetid: 9bc881b3-e2ce-48a7-ad69-17eaaa304120
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b0b2ce6facf99b44f54e8880d4436ab7fe96e50a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocumentgetchecksum-method"></a><span data-ttu-id="4b777-102">ISymUnmanagedDocument::GetCheckSum 方法</span><span class="sxs-lookup"><span data-stu-id="4b777-102">ISymUnmanagedDocument::GetCheckSum Method</span></span>
<span data-ttu-id="4b777-103">取得總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="4b777-103">Gets the checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b777-104">語法</span><span class="sxs-lookup"><span data-stu-id="4b777-104">Syntax</span></span>  
  
```  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4b777-105">參數</span><span class="sxs-lookup"><span data-stu-id="4b777-105">Parameters</span></span>  
 `cData`  
 <span data-ttu-id="4b777-106">[in]所提供的緩衝區長度`data`參數</span><span class="sxs-lookup"><span data-stu-id="4b777-106">[in] The length of the buffer provided by the `data` parameter</span></span>  
  
 `pcData`  
 <span data-ttu-id="4b777-107">[out]大小和總和檢查碼，以位元組為單位的長度。</span><span class="sxs-lookup"><span data-stu-id="4b777-107">[out] The size and length of the checksum, in bytes.</span></span>  
  
 `data`  
 <span data-ttu-id="4b777-108">[out]接收總和檢查碼的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="4b777-108">[out] The buffer that receives the checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4b777-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="4b777-109">Return Value</span></span>  
 <span data-ttu-id="4b777-110">如果方法成功則為 S_OK否則，錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="4b777-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b777-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b777-111">See Also</span></span>  
 [<span data-ttu-id="4b777-112">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="4b777-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
