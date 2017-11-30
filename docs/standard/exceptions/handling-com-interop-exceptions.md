---
title: "處理 COM Interop 例外狀況"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: error-reference
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- HRESULTs
- exceptions, COM interop
- COM interop, exceptions
ms.assetid: e6104aa8-8e5f-4069-b864-def85579c96c
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bc3e01bc8ca463460ede9544d1d5c095c39a59d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="handling-com-interop-exceptions"></a><span data-ttu-id="76e17-102">處理 COM Interop 例外狀況</span><span class="sxs-lookup"><span data-stu-id="76e17-102">Handling COM Interop Exceptions</span></span>
<span data-ttu-id="76e17-103">Managed 和 Unmanaged 程式碼可一起運作來處理例外狀況。</span><span class="sxs-lookup"><span data-stu-id="76e17-103">Managed and unmanaged code can work together to handle exceptions.</span></span> <span data-ttu-id="76e17-104">如果方法在 Managed 程式碼擲回例外狀況，則 Common Language Runtime 可以傳遞 HRESULT 給 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="76e17-104">If a method throws an exception in managed code, the common language runtime can pass an HRESULT to a COM object.</span></span> <span data-ttu-id="76e17-105">如果在 Unmanaged 程式碼中的方法藉由傳回失敗 HRESULT 而失敗，則執行階段會擲回 Managed 程式碼可以攔截的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="76e17-105">If a method fails in unmanaged code by returning a failure HRESULT, the runtime throws an exception that can be caught by managed code.</span></span>  
  
 <span data-ttu-id="76e17-106">執行階段會自動將 HRESULT 從 COM Interop 對應至更特定的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="76e17-106">The runtime automatically maps the HRESULT from COM interop to more specific exceptions.</span></span> <span data-ttu-id="76e17-107">例如，E_ACCESSDENIED 會變成 <xref:System.UnauthorizedAccessException>，而 E_OUTOFMEMORY 變成 <xref:System.OutOfMemoryException> 等等。</span><span class="sxs-lookup"><span data-stu-id="76e17-107">For example, E_ACCESSDENIED becomes <xref:System.UnauthorizedAccessException>, E_OUTOFMEMORY becomes <xref:System.OutOfMemoryException>, and so on.</span></span>  
  
 <span data-ttu-id="76e17-108">如果 HRESULT 是自訂的結果，或者它對於執行階段是未知的，則執行階段會傳遞泛型 <xref:System.Runtime.InteropServices.COMException> 給用戶端。</span><span class="sxs-lookup"><span data-stu-id="76e17-108">If the HRESULT is a custom result or if it is unknown to the runtime, the runtime passes a generic <xref:System.Runtime.InteropServices.COMException> to the client.</span></span> <span data-ttu-id="76e17-109">**ErrorCode**屬性**COMException**包含 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="76e17-109">The **ErrorCode** property of the **COMException** contains the HRESULT value.</span></span>  
  
## <a name="working-with-ierrorinfo"></a><span data-ttu-id="76e17-110">使用 IErrorInfo</span><span class="sxs-lookup"><span data-stu-id="76e17-110">Working with IErrorInfo</span></span>  
 <span data-ttu-id="76e17-111">當錯誤從 COM 傳遞至 Managed 程式碼時，執行階段會填入錯誤資訊至例外狀況物件。</span><span class="sxs-lookup"><span data-stu-id="76e17-111">When an error is passed from COM to managed code, the runtime populates the exception object with error information.</span></span> <span data-ttu-id="76e17-112">支援 IErrorInfo 且傳回 HRESULT 的 COM 物件會提供這項資訊給 Managed 程式碼例外狀況。</span><span class="sxs-lookup"><span data-stu-id="76e17-112">COM objects that support IErrorInfo and return HRESULTS provide this information to managed code exceptions.</span></span> <span data-ttu-id="76e17-113">例如，執行階段從 COM 錯誤對應描述至例外狀況的 <xref:System.Exception.Message%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="76e17-113">For example, the runtime maps the Description from the COM error to the exception's <xref:System.Exception.Message%2A> property.</span></span> <span data-ttu-id="76e17-114">如果 HRESULT 沒有提供其他錯誤資訊，則執行階段會填滿預設值到許多例外狀況的屬性。</span><span class="sxs-lookup"><span data-stu-id="76e17-114">If the HRESULT provides no additional error information, the runtime fills many of the exception's properties with default values.</span></span>  
  
 <span data-ttu-id="76e17-115">如果在 Unmanaged 程式碼中的方法失敗，則例外狀況可以傳遞至 Managed 程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="76e17-115">If a method fails in unmanaged code, an exception can be passed to a managed code segment.</span></span> <span data-ttu-id="76e17-116">本主題[HRESULT 和例外狀況](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md)包含資料表顯示 HRESULT 如何對應至執行階段例外狀況物件。</span><span class="sxs-lookup"><span data-stu-id="76e17-116">The topic [HRESULTS and Exceptions](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) contains a table showing how HRESULTS map to runtime exception objects.</span></span>  

## <a name="see-also"></a><span data-ttu-id="76e17-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76e17-117">See Also</span></span>
[<span data-ttu-id="76e17-118">例外狀況</span><span class="sxs-lookup"><span data-stu-id="76e17-118">Exceptions</span></span>](index.md) 
