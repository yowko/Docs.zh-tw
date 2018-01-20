---
title: "如何：呼叫 Windows API (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 772db789fba4552a4645d2c6a242ba01944652ee
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-call-windows-apis-visual-basic"></a><span data-ttu-id="872cc-102">如何：呼叫 Windows API (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="872cc-102">How to: Call Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="872cc-103">此範例中定義，並呼叫`MessageBox`user32.dll 中的函式，然後將字串傳遞給它。</span><span class="sxs-lookup"><span data-stu-id="872cc-103">This example defines and calls the `MessageBox` function in user32.dll and then passes a string to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="872cc-104">範例</span><span class="sxs-lookup"><span data-stu-id="872cc-104">Example</span></span>  
 [!code-vb[VbVbalrInterop#1](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-call-windows-apis_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="872cc-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="872cc-105">Compiling the Code</span></span>  
 <span data-ttu-id="872cc-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="872cc-106">This example requires:</span></span>  
  
-   <span data-ttu-id="872cc-107"><xref:System> 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="872cc-107">A reference to the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="872cc-108">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="872cc-108">Robust Programming</span></span>  
 <span data-ttu-id="872cc-109">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="872cc-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="872cc-110">此方法不是靜態、 是抽象的或先前已定義。</span><span class="sxs-lookup"><span data-stu-id="872cc-110">The method is not static, is abstract, or has been previously defined.</span></span> <span data-ttu-id="872cc-111">父類型是介面或長度*名稱*或*dllName*為零。</span><span class="sxs-lookup"><span data-stu-id="872cc-111">The parent type is an interface, or the length of *name* or *dllName* is zero.</span></span> <span data-ttu-id="872cc-112">(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="872cc-112">(<xref:System.ArgumentException>)</span></span>  
  
-   <span data-ttu-id="872cc-113">*名稱*或*dllName*是`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="872cc-113">The *name* or *dllName* is `Nothing`.</span></span> <span data-ttu-id="872cc-114">(<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="872cc-114">(<xref:System.ArgumentNullException>)</span></span>  
  
-   <span data-ttu-id="872cc-115">之前已使用 `CreateType` 建立包含類型。</span><span class="sxs-lookup"><span data-stu-id="872cc-115">The containing type has been previously created using `CreateType`.</span></span> <span data-ttu-id="872cc-116">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="872cc-116">(<xref:System.InvalidOperationException>)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="872cc-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="872cc-117">See Also</span></span>  
 [<span data-ttu-id="872cc-118">詳述平台叫用</span><span class="sxs-lookup"><span data-stu-id="872cc-118">A Closer Look at Platform Invoke</span></span>](http://msdn.microsoft.com/library/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)  
 [<span data-ttu-id="872cc-119">平台叫用範例</span><span class="sxs-lookup"><span data-stu-id="872cc-119">Platform Invoke Examples</span></span>](../../../framework/interop/platform-invoke-examples.md)  
 [<span data-ttu-id="872cc-120">使用 Unmanaged DLL 函式</span><span class="sxs-lookup"><span data-stu-id="872cc-120">Consuming Unmanaged DLL Functions</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md)  
 [<span data-ttu-id="872cc-121">定義方法，以使用反映發出</span><span class="sxs-lookup"><span data-stu-id="872cc-121">Defining a Method with Reflection Emit</span></span>](http://msdn.microsoft.com/library/84fd3bf6-628f-41aa-83d9-b990cf926e81)  
 [<span data-ttu-id="872cc-122">逐步解說：呼叫 Windows API</span><span class="sxs-lookup"><span data-stu-id="872cc-122">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 [<span data-ttu-id="872cc-123">COM Interop</span><span class="sxs-lookup"><span data-stu-id="872cc-123">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)
