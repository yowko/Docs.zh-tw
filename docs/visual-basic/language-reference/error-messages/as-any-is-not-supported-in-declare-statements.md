---
title: "&quot;As Any&quot; 是 &quot;Declare&quot; 陳述式不支援 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30828
- vbc30828
dev_langs:
- VB
helpviewer_keywords:
- BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: bed9beb0c34c1a918029cc7fac4f8c97950eee23
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="39as-any39-is-not-supported-in-39declare39-statements"></a><span data-ttu-id="cc607-102">'As Any' 不支援 'Declare' 陳述式中</span><span class="sxs-lookup"><span data-stu-id="cc607-102">&#39;As Any&#39; is not supported in &#39;Declare&#39; statements</span></span>
<span data-ttu-id="cc607-103">`Any`資料類型用於`Declare`允許無法包含任何資料類型的引數使用的 Visual Basic 6.0 及舊版中的陳述式。</span><span class="sxs-lookup"><span data-stu-id="cc607-103">The `Any` data type was used with `Declare` statements in Visual Basic 6.0 and earlier versions to permit the use of arguments that could contain any type of data.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="cc607-104">多載，不過，支援，因此讓`Any`資料型別已經過時。</span><span class="sxs-lookup"><span data-stu-id="cc607-104"> supports overloading, however, and so makes the `Any` data type obsolete.</span></span>  
  
 <span data-ttu-id="cc607-105">**錯誤識別碼︰** BC30828</span><span class="sxs-lookup"><span data-stu-id="cc607-105">**Error ID:** BC30828</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cc607-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="cc607-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="cc607-107">宣告參數的特定型別，您想要使用;例如。</span><span class="sxs-lookup"><span data-stu-id="cc607-107">Declare parameters of the specific type you want to use; for example.</span></span>  
  
     <span data-ttu-id="cc607-108">[!code-vb[VbVbalrStatements #&95;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="cc607-108">[!code-vb[VbVbalrStatements#95](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_1.vb)]</span></span>  
  
2.  <span data-ttu-id="cc607-109">使用<xref:System.Runtime.InteropServices.MarshalAsAttribute>屬性來指定`As Any`時`Void*`所呼叫的程序所預期。</xref:System.Runtime.InteropServices.MarshalAsAttribute></span><span class="sxs-lookup"><span data-stu-id="cc607-109">Use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to specify `As Any` when `Void*` is expected by the procedure being called.</span></span>  
  
     <span data-ttu-id="cc607-110">[!code-vb[VbVbalrStatements #&96;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="cc607-110">[!code-vb[VbVbalrStatements#96](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc607-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc607-111">See Also</span></span>  
 <span data-ttu-id="cc607-112"><xref:System.Runtime.InteropServices.MarshalAsAttribute></xref:System.Runtime.InteropServices.MarshalAsAttribute></span><span class="sxs-lookup"><span data-stu-id="cc607-112"><xref:System.Runtime.InteropServices.MarshalAsAttribute></span></span>   
<span data-ttu-id="cc607-113"> [逐步解說︰ 呼叫 Windows Api](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md) </span><span class="sxs-lookup"><span data-stu-id="cc607-113"> [Walkthrough: Calling Windows APIs](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md) </span></span>  
<span data-ttu-id="cc607-114"> [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md) </span><span class="sxs-lookup"><span data-stu-id="cc607-114"> [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) </span></span>  
<span data-ttu-id="cc607-115"> [在 Managed 程式碼中建立原型](http://msdn.microsoft.com/library/ecdcf25d-cae3-4f07-a2b6-8397ac6dc42d)</span><span class="sxs-lookup"><span data-stu-id="cc607-115"> [Creating Prototypes in Managed Code](http://msdn.microsoft.com/library/ecdcf25d-cae3-4f07-a2b6-8397ac6dc42d)</span></span>
