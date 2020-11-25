---
title: ISymENCUnmanagedMethod 介面
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod
helpviewer_keywords:
- ISymENCUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: faebf594-67d5-4abf-b9c1-547fd3a1ff87
topic_type:
- apiref
ms.openlocfilehash: acb8d48ed6314756e2c1a10fff314a303799fb24
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707278"
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="268d4-102">ISymENCUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="268d4-102">ISymENCUnmanagedMethod Interface</span></span>

<span data-ttu-id="268d4-103">提供 [編輯後繼續] 功能的資訊。</span><span class="sxs-lookup"><span data-stu-id="268d4-103">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="268d4-104">方法</span><span class="sxs-lookup"><span data-stu-id="268d4-104">Methods</span></span>  
  
|<span data-ttu-id="268d4-105">方法</span><span class="sxs-lookup"><span data-stu-id="268d4-105">Method</span></span>|<span data-ttu-id="268d4-106">描述</span><span class="sxs-lookup"><span data-stu-id="268d4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="268d4-107">GetDocumentsForMethod 方法</span><span class="sxs-lookup"><span data-stu-id="268d4-107">GetDocumentsForMethod Method</span></span>](isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="268d4-108">取得此方法具有行的檔。</span><span class="sxs-lookup"><span data-stu-id="268d4-108">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="268d4-109">GetDocumentsForMethodCount 方法</span><span class="sxs-lookup"><span data-stu-id="268d4-109">GetDocumentsForMethodCount Method</span></span>](isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="268d4-110">取得此方法具有行的檔數目。</span><span class="sxs-lookup"><span data-stu-id="268d4-110">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="268d4-111">GetFileNameFromOffset 方法</span><span class="sxs-lookup"><span data-stu-id="268d4-111">GetFileNameFromOffset Method</span></span>](isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="268d4-112">取得與位移相關聯之線條的檔案名。</span><span class="sxs-lookup"><span data-stu-id="268d4-112">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="268d4-113">GetLineFromOffset 方法</span><span class="sxs-lookup"><span data-stu-id="268d4-113">GetLineFromOffset Method</span></span>](isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="268d4-114">取得與位移相關聯的行資訊。</span><span class="sxs-lookup"><span data-stu-id="268d4-114">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="268d4-115">GetSourceExtentInDocument 方法</span><span class="sxs-lookup"><span data-stu-id="268d4-115">GetSourceExtentInDocument Method</span></span>](isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="268d4-116">取得特定檔中方法的最小開始行和最大結束行。</span><span class="sxs-lookup"><span data-stu-id="268d4-116">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="268d4-117">需求</span><span class="sxs-lookup"><span data-stu-id="268d4-117">Requirements</span></span>  

 <span data-ttu-id="268d4-118">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="268d4-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="268d4-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="268d4-119">See also</span></span>

- [<span data-ttu-id="268d4-120">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="268d4-120">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
