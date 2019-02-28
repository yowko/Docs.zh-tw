---
title: "'Declare' 陳述式中不支援 'As Any'"
ms.date: 07/20/2015
f1_keywords:
- bc30828
- vbc30828
helpviewer_keywords:
- BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
ms.openlocfilehash: b3fb3f208f3396f454388ec0c10406815fa957d8
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974792"
---
# <a name="as-any-is-not-supported-in-declare-statements"></a><span data-ttu-id="e0b4f-102">'Declare' 陳述式中不支援 'As Any'</span><span class="sxs-lookup"><span data-stu-id="e0b4f-102">'As Any' is not supported in 'Declare' statements</span></span>
<span data-ttu-id="e0b4f-103">`Any`資料類型用於`Declare`允許無法包含任何資料類型的引數使用的 Visual Basic 6.0 和更早版本中的陳述式。</span><span class="sxs-lookup"><span data-stu-id="e0b4f-103">The `Any` data type was used with `Declare` statements in Visual Basic 6.0 and earlier versions to permit the use of arguments that could contain any type of data.</span></span> <span data-ttu-id="e0b4f-104">Visual Basic 支援多載，不過，並因此會`Any`資料型別已經過時。</span><span class="sxs-lookup"><span data-stu-id="e0b4f-104">Visual Basic supports overloading, however, and so makes the `Any` data type obsolete.</span></span>  
  
 <span data-ttu-id="e0b4f-105">**錯誤 ID:** BC30828</span><span class="sxs-lookup"><span data-stu-id="e0b4f-105">**Error ID:** BC30828</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e0b4f-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="e0b4f-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="e0b4f-107">宣告您想要使用的特定型別參數比方說。</span><span class="sxs-lookup"><span data-stu-id="e0b4f-107">Declare parameters of the specific type you want to use; for example.</span></span>  
  
     [!code-vb[VbVbalrStatements#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class5.vb#95)]  
  
2.  <span data-ttu-id="e0b4f-108">使用<xref:System.Runtime.InteropServices.MarshalAsAttribute>屬性來指定`As Any`當`Void*`預期的被呼叫程序。</span><span class="sxs-lookup"><span data-stu-id="e0b4f-108">Use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to specify `As Any` when `Void*` is expected by the procedure being called.</span></span>  
  
     [!code-vb[VbVbalrStatements#96](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class5.vb#96)]  
  
## <a name="see-also"></a><span data-ttu-id="e0b4f-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0b4f-109">See also</span></span>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="e0b4f-110">逐步解說：呼叫 Windows API</span><span class="sxs-lookup"><span data-stu-id="e0b4f-110">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [<span data-ttu-id="e0b4f-111">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="e0b4f-111">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="e0b4f-112">在 Managed 程式碼中建立原型</span><span class="sxs-lookup"><span data-stu-id="e0b4f-112">Creating Prototypes in Managed Code</span></span>](../../../framework/interop/creating-prototypes-in-managed-code.md)
