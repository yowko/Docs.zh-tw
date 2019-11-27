---
title: 如何：驗證代表日期或時間的字串
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 34af6dffeb0d05eaeed38354f8007554b60e91b0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344347"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a><span data-ttu-id="bd8de-102">如何：驗證代表日期或時間的字串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd8de-102">How to: Validate Strings That Represent Dates or Times (Visual Basic)</span></span>
<span data-ttu-id="bd8de-103">下列程式碼範例會設定 `Boolean` 值，指出字串是否代表有效的日期或時間。</span><span class="sxs-lookup"><span data-stu-id="bd8de-103">The following code example sets a `Boolean` value that indicates whether a string represents a valid date or time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd8de-104">範例</span><span class="sxs-lookup"><span data-stu-id="bd8de-104">Example</span></span>  
 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bd8de-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="bd8de-105">Compiling the Code</span></span>  
 <span data-ttu-id="bd8de-106">以您想要驗證的日期和時間取代 `("01/01/03")` 和 `"9:30 PM"`。</span><span class="sxs-lookup"><span data-stu-id="bd8de-106">Replace `("01/01/03")` and `"9:30 PM"` with the date and time you want to validate.</span></span> <span data-ttu-id="bd8de-107">您可以使用另一個硬式編碼字串、`String` 變數或傳回字串的方法（例如 `InputBox`）來取代字串。</span><span class="sxs-lookup"><span data-stu-id="bd8de-107">You can replace the string with another hard-coded string, with a `String` variable, or with a method that returns a string, such as `InputBox`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="bd8de-108">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="bd8de-108">Robust Programming</span></span>  
 <span data-ttu-id="bd8de-109">嘗試將 `String` 轉換成 `DateTime` 變數之前，請使用這個方法來驗證字串。</span><span class="sxs-lookup"><span data-stu-id="bd8de-109">Use this method to validate the string before trying to convert the `String` to a `DateTime` variable.</span></span> <span data-ttu-id="bd8de-110">藉由先檢查日期或時間，您可以避免在執行時間產生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bd8de-110">By checking the date or time first, you can avoid generating an exception at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd8de-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="bd8de-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [<span data-ttu-id="bd8de-112">在 Visual Basic 中驗證字串</span><span class="sxs-lookup"><span data-stu-id="bd8de-112">Validating Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
