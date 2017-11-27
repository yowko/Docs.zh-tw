---
title: "ISymUnmanagedWriter::SetUserEntryPoint 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.SetUserEntryPoint
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::SetUserEntryPoint
helpviewer_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint method [.NET Framework debugging]
- SetUserEntryPoint method [.NET Framework debugging]
ms.assetid: d4dcc575-3ac8-4453-9be1-2b24f47363d7
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: be7f348237fdcf0a136d34ce3b6b8548c16d5547
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a><span data-ttu-id="a5aa1-102">ISymUnmanagedWriter::SetUserEntryPoint 方法</span><span class="sxs-lookup"><span data-stu-id="a5aa1-102">ISymUnmanagedWriter::SetUserEntryPoint Method</span></span>
<span data-ttu-id="a5aa1-103">指定的使用者定義的方法，是針對此模組的進入點。</span><span class="sxs-lookup"><span data-stu-id="a5aa1-103">Specifies the user-defined method that is the entry point for this module.</span></span> <span data-ttu-id="a5aa1-104">比方說，此進入點可能是使用者的主要方法，而不是在 main 之前編譯器產生的虛設常式。</span><span class="sxs-lookup"><span data-stu-id="a5aa1-104">For example, this entry point could be the user's main method instead of compiler-generated stubs before main.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5aa1-105">語法</span><span class="sxs-lookup"><span data-stu-id="a5aa1-105">Syntax</span></span>  
  
```  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a5aa1-106">參數</span><span class="sxs-lookup"><span data-stu-id="a5aa1-106">Parameters</span></span>  
 `entryMethod`  
 <span data-ttu-id="a5aa1-107">[in]中繼資料語彙基元的方法，是使用者進入點。</span><span class="sxs-lookup"><span data-stu-id="a5aa1-107">[in] The metadata token for the method that is the user entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a5aa1-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="a5aa1-108">Return Value</span></span>  
 <span data-ttu-id="a5aa1-109">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="a5aa1-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5aa1-110">需求</span><span class="sxs-lookup"><span data-stu-id="a5aa1-110">Requirements</span></span>  
 <span data-ttu-id="a5aa1-111">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a5aa1-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5aa1-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5aa1-112">See Also</span></span>  
 [<span data-ttu-id="a5aa1-113">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="a5aa1-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
