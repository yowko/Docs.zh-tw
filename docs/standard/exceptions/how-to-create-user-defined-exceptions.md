---
title: "如何：建立使用者定義的例外狀況"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- user-defined exceptions
- exceptions, examples
- exceptions, user-defined
ms.assetid: 25819a5a-f915-4fc8-b924-a76915674e04
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c55489a4c0b86142fcda99c5962c896b73691cd6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-create-user-defined-exceptions"></a><span data-ttu-id="663cd-102">如何建立使用者定義的例外狀況</span><span class="sxs-lookup"><span data-stu-id="663cd-102">How to create user-defined exceptions</span></span>

<span data-ttu-id="663cd-103">.NET 提供基本上衍生自基底類別 <xref:System.Exception> 之例外狀況類別的階層架構。</span><span class="sxs-lookup"><span data-stu-id="663cd-103">.NET provides a hierarchy of exception classes ultimately derived from the base class <xref:System.Exception>.</span></span> <span data-ttu-id="663cd-104">不過，如果沒有預先定義的例外狀況符合您的需求，您可以藉由衍生自 <xref:System.Exception> 類別，建立您自己的例外狀況類別。</span><span class="sxs-lookup"><span data-stu-id="663cd-104">However, if none of the predefined exceptions meets your needs, you can create your own exception classes by deriving from the <xref:System.Exception> class.</span></span>

<span data-ttu-id="663cd-105">建立您自己的例外狀況時，以文字 "Exception" 作為使用者定義例外狀況類別名稱的結尾，並實作三種常見的建構函式，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="663cd-105">When creating your own exceptions, end the class name of the user-defined exception with the word "Exception," and implement the three common constructors, as shown in the following example.</span></span> <span data-ttu-id="663cd-106">此範例會定義名為 `EmployeeListNotFoundException` 的新例外狀況類別。</span><span class="sxs-lookup"><span data-stu-id="663cd-106">The example defines a new exception class named `EmployeeListNotFoundException`.</span></span> <span data-ttu-id="663cd-107">此類別衍生自 <xref:System.Exception>，包含三個建構函式。</span><span class="sxs-lookup"><span data-stu-id="663cd-107">The class is derived from <xref:System.Exception> and includes three constructors.</span></span>

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> <span data-ttu-id="663cd-108">在您使用遠端功能的情況下，您必須確定任何使用者定義例外狀況的中繼資料是由伺服器 (被呼叫端) 提供，並提供給用戶端 (Proxy 物件或呼叫端)。</span><span class="sxs-lookup"><span data-stu-id="663cd-108">In situations where you are using remoting, you must ensure that the metadata for any user-defined exceptions is available at the server (callee) and to the client (the proxy object or caller).</span></span> <span data-ttu-id="663cd-109">如需詳細資訊，請參閱[例外狀況的最佳做法](best-practices-for-exceptions.md)。</span><span class="sxs-lookup"><span data-stu-id="663cd-109">For more information, see [Best practices for exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="663cd-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="663cd-110">See Also</span></span>  
[<span data-ttu-id="663cd-111">例外狀況</span><span class="sxs-lookup"><span data-stu-id="663cd-111">Exceptions</span></span>](index.md)
