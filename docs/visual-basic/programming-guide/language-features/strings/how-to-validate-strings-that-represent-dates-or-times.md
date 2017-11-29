---
title: "如何：驗證代表日期或時間的字串 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ed3201ef2bbef97eebbafa5ef128ca015adac013
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a><span data-ttu-id="d0f48-102">如何：驗證代表日期或時間的字串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0f48-102">How to: Validate Strings That Represent Dates or Times (Visual Basic)</span></span>
<span data-ttu-id="d0f48-103">下列程式碼範例會設定`Boolean`值，指出字串是否表示有效的日期或時間。</span><span class="sxs-lookup"><span data-stu-id="d0f48-103">The following code example sets a `Boolean` value that indicates whether a string represents a valid date or time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0f48-104">範例</span><span class="sxs-lookup"><span data-stu-id="d0f48-104">Example</span></span>  
 [!code-vb[VbVbcnRegEx#2](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-strings-that-represent-dates-or-times_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d0f48-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="d0f48-105">Compiling the Code</span></span>  
 <span data-ttu-id="d0f48-106">取代`("01/01/03")`和`"9:30 PM"`與您想要驗證的時間與日期。</span><span class="sxs-lookup"><span data-stu-id="d0f48-106">Replace `("01/01/03")` and `"9:30 PM"` with the date and time you want to validate.</span></span> <span data-ttu-id="d0f48-107">您可以取代其他硬式編碼字串的字串`String`變數，或使用的方法，傳回字串，例如`InputBox`。</span><span class="sxs-lookup"><span data-stu-id="d0f48-107">You can replace the string with another hard-coded string, with a `String` variable, or with a method that returns a string, such as `InputBox`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d0f48-108">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="d0f48-108">Robust Programming</span></span>  
 <span data-ttu-id="d0f48-109">使用這個方法來驗證該字串，然後再嘗試轉換`String`至`DateTime`變數。</span><span class="sxs-lookup"><span data-stu-id="d0f48-109">Use this method to validate the string before trying to convert the `String` to a `DateTime` variable.</span></span> <span data-ttu-id="d0f48-110">您可以藉由先檢查日期或時間，避免產生在執行階段例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d0f48-110">By checking the date or time first, you can avoid generating an exception at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0f48-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0f48-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Information.IsDate%2A>  
 <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>  
 [<span data-ttu-id="d0f48-112">在 Visual Basic 中驗證字串</span><span class="sxs-lookup"><span data-stu-id="d0f48-112">Validating Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
