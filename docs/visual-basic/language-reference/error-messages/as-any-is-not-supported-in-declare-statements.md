---
title: "&#39;做為任何 &#39;不支援 &#39; Declare &#39;陳述式"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30828
- vbc30828
helpviewer_keywords: BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 59120622688ee38d5b8f45c08dfc3ae40711fb8b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="39as-any39-is-not-supported-in-39declare39-statements"></a><span data-ttu-id="15d95-102">&#39;做為任何 &#39;不支援 &#39; Declare &#39;陳述式</span><span class="sxs-lookup"><span data-stu-id="15d95-102">&#39;As Any&#39; is not supported in &#39;Declare&#39; statements</span></span>
<span data-ttu-id="15d95-103">`Any`資料類型用於`Declare`允許無法包含任何資料類型的引數使用的 Visual Basic 6.0 及舊版中的陳述式。</span><span class="sxs-lookup"><span data-stu-id="15d95-103">The `Any` data type was used with `Declare` statements in Visual Basic 6.0 and earlier versions to permit the use of arguments that could contain any type of data.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="15d95-104">多載，不過，支援，因此讓`Any`資料型別已經過時。</span><span class="sxs-lookup"><span data-stu-id="15d95-104"> supports overloading, however, and so makes the `Any` data type obsolete.</span></span>  
  
 <span data-ttu-id="15d95-105">**錯誤 ID:** BC30828</span><span class="sxs-lookup"><span data-stu-id="15d95-105">**Error ID:** BC30828</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="15d95-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="15d95-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="15d95-107">宣告您想要使用; 的特定型別參數如需範例。</span><span class="sxs-lookup"><span data-stu-id="15d95-107">Declare parameters of the specific type you want to use; for example.</span></span>  
  
     [!code-vb[VbVbalrStatements#95](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_1.vb)]  
  
2.  <span data-ttu-id="15d95-108">使用<xref:System.Runtime.InteropServices.MarshalAsAttribute>屬性來指定`As Any`時`Void*`必須由被呼叫程序。</span><span class="sxs-lookup"><span data-stu-id="15d95-108">Use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to specify `As Any` when `Void*` is expected by the procedure being called.</span></span>  
  
     [!code-vb[VbVbalrStatements#96](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="15d95-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15d95-109">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="15d95-110">逐步解說：呼叫 Windows API</span><span class="sxs-lookup"><span data-stu-id="15d95-110">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 [<span data-ttu-id="15d95-111">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="15d95-111">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="15d95-112">在 Managed 程式碼中建立原型</span><span class="sxs-lookup"><span data-stu-id="15d95-112">Creating Prototypes in Managed Code</span></span>](../../../framework/interop/creating-prototypes-in-managed-code.md)
