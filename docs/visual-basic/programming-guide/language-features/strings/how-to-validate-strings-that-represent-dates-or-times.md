---
title: 如何：驗證代表日期或時間的字串
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: f3654894e274404410179dab04422e20f6040440
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072596"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a><span data-ttu-id="8518c-102">如何：驗證代表日期或時間的字串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8518c-102">How to: Validate Strings That Represent Dates or Times (Visual Basic)</span></span>

<span data-ttu-id="8518c-103">下列程式碼範例會設定一個 `Boolean` 值，指出字串是否代表有效的日期或時間。</span><span class="sxs-lookup"><span data-stu-id="8518c-103">The following code example sets a `Boolean` value that indicates whether a string represents a valid date or time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8518c-104">範例</span><span class="sxs-lookup"><span data-stu-id="8518c-104">Example</span></span>  

 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="8518c-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="8518c-105">Compile the code</span></span>  

 <span data-ttu-id="8518c-106">`("01/01/03")`將和取代為 `"9:30 PM"` 您想要驗證的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="8518c-106">Replace `("01/01/03")` and `"9:30 PM"` with the date and time you want to validate.</span></span> <span data-ttu-id="8518c-107">您可以使用另一個硬式編碼的字串、變數或傳回字串的方法（例如）來取代字串 `String` `InputBox` 。</span><span class="sxs-lookup"><span data-stu-id="8518c-107">You can replace the string with another hard-coded string, with a `String` variable, or with a method that returns a string, such as `InputBox`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="8518c-108">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="8518c-108">Robust Programming</span></span>  

 <span data-ttu-id="8518c-109">您可以使用這個方法來驗證字串，然後再嘗試將轉換成 `String` `DateTime` 變數。</span><span class="sxs-lookup"><span data-stu-id="8518c-109">Use this method to validate the string before trying to convert the `String` to a `DateTime` variable.</span></span> <span data-ttu-id="8518c-110">藉由先檢查日期或時間，您可以避免在執行時間產生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8518c-110">By checking the date or time first, you can avoid generating an exception at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8518c-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8518c-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [<span data-ttu-id="8518c-112">在 Visual Basic 中驗證字串</span><span class="sxs-lookup"><span data-stu-id="8518c-112">Validating Strings in Visual Basic</span></span>](validating-strings.md)
