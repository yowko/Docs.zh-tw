---
title: 如何：驗證代表日期或時間的字串
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 5d153ac29039375386b3cd5f03609b1e4bd1d5bf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410563"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a><span data-ttu-id="0969a-102">如何：驗證代表日期或時間的字串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0969a-102">How to: Validate Strings That Represent Dates or Times (Visual Basic)</span></span>
<span data-ttu-id="0969a-103">下列程式碼範例會設定一個 `Boolean` 值，指出字串是否代表有效的日期或時間。</span><span class="sxs-lookup"><span data-stu-id="0969a-103">The following code example sets a `Boolean` value that indicates whether a string represents a valid date or time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0969a-104">範例</span><span class="sxs-lookup"><span data-stu-id="0969a-104">Example</span></span>  
 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="0969a-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="0969a-105">Compile the code</span></span>  
 <span data-ttu-id="0969a-106">`("01/01/03")`將和取代為 `"9:30 PM"` 您想要驗證的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="0969a-106">Replace `("01/01/03")` and `"9:30 PM"` with the date and time you want to validate.</span></span> <span data-ttu-id="0969a-107">您可以使用 `String` 變數或傳回字串的方法（例如），將字串取代為另一個硬式編碼的字串。 `InputBox`</span><span class="sxs-lookup"><span data-stu-id="0969a-107">You can replace the string with another hard-coded string, with a `String` variable, or with a method that returns a string, such as `InputBox`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="0969a-108">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="0969a-108">Robust Programming</span></span>  
 <span data-ttu-id="0969a-109">嘗試將轉換成變數之前，請使用這個方法來驗證字串 `String` `DateTime` 。</span><span class="sxs-lookup"><span data-stu-id="0969a-109">Use this method to validate the string before trying to convert the `String` to a `DateTime` variable.</span></span> <span data-ttu-id="0969a-110">藉由先檢查日期或時間，您可以避免在執行時間產生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0969a-110">By checking the date or time first, you can avoid generating an exception at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0969a-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0969a-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [<span data-ttu-id="0969a-112">在 Visual Basic 中驗證字串</span><span class="sxs-lookup"><span data-stu-id="0969a-112">Validating Strings in Visual Basic</span></span>](validating-strings.md)
