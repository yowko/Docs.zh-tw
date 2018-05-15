---
title: 驗證密碼複雜性 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: acfc8ab958c8671ed7f1afd245d24a43ca12be29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a><span data-ttu-id="d9ad7-102">逐步解說：驗證密碼確實複雜 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9ad7-102">Walkthrough: Validating That Passwords Are Complex (Visual Basic)</span></span>
<span data-ttu-id="d9ad7-103">這個方法會檢查有某些強式密碼特性，並更新有關哪些檢查密碼失敗的資訊的字串參數。</span><span class="sxs-lookup"><span data-stu-id="d9ad7-103">This method checks for some strong-password characteristics and updates a string parameter with information about which checks the password fails.</span></span>  
  
 <span data-ttu-id="d9ad7-104">密碼可以用在安全的系統，來授權使用者。</span><span class="sxs-lookup"><span data-stu-id="d9ad7-104">Passwords can be used in a secure system to authorize a user.</span></span> <span data-ttu-id="d9ad7-105">不過，密碼必須是難以猜測未經授權的使用者。</span><span class="sxs-lookup"><span data-stu-id="d9ad7-105">However, the passwords must be difficult for unauthorized users to guess.</span></span> <span data-ttu-id="d9ad7-106">攻擊者能夠使用*字典攻擊*程式，可逐一查看所有字典 （或以不同語言的多個字典） 中的文字，並測試是否有任何文字做為使用者的密碼。</span><span class="sxs-lookup"><span data-stu-id="d9ad7-106">Attackers can use a *dictionary attack* program, which iterates through all of the words in a dictionary (or multiple dictionaries in different languages) and tests whether any of the words work as a user's password.</span></span> <span data-ttu-id="d9ad7-107">弱式密碼，例如"洋基隊"或"Mustang 」 可以快速猜測。</span><span class="sxs-lookup"><span data-stu-id="d9ad7-107">Weak passwords such as "Yankees" or "Mustang" can be guessed quickly.</span></span> <span data-ttu-id="d9ad7-108">更強的密碼，例如"嗎？您 'L1N3vaFiNdMeyeP@sSWerd！"，較可能被猜到。</span><span class="sxs-lookup"><span data-stu-id="d9ad7-108">Stronger passwords, such as "?You'L1N3vaFiNdMeyeP@sSWerd!", are much less likely to be guessed.</span></span> <span data-ttu-id="d9ad7-109">受密碼保護的系統，應該確保使用者選擇強式密碼。</span><span class="sxs-lookup"><span data-stu-id="d9ad7-109">A password-protected system should ensure that users choose strong passwords.</span></span>  
  
 <span data-ttu-id="d9ad7-110">強式密碼很複雜 （包含大寫、 小寫、 數字及特殊字元的混合），而且不是字。</span><span class="sxs-lookup"><span data-stu-id="d9ad7-110">A strong password is complex (containing a mixture of uppercase, lowercase, numeric, and special characters) and is not a word.</span></span> <span data-ttu-id="d9ad7-111">此範例示範如何驗證複雜性。</span><span class="sxs-lookup"><span data-stu-id="d9ad7-111">This example demonstrates how to verify complexity.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9ad7-112">範例</span><span class="sxs-lookup"><span data-stu-id="d9ad7-112">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="d9ad7-113">程式碼</span><span class="sxs-lookup"><span data-stu-id="d9ad7-113">Code</span></span>  
 [!code-vb[VbVbcnRegEx#1](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/walkthrough-validating-that-passwords-are-complex_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d9ad7-114">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="d9ad7-114">Compiling the Code</span></span>  
 <span data-ttu-id="d9ad7-115">呼叫這個方法由傳遞字串，包含該密碼。</span><span class="sxs-lookup"><span data-stu-id="d9ad7-115">Call this method by passing the string that contains that password.</span></span>  
  
 <span data-ttu-id="d9ad7-116">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="d9ad7-116">This example requires:</span></span>  
  
-   <span data-ttu-id="d9ad7-117"><xref:System.Text.RegularExpressions> 命名空間成員的存取權。</span><span class="sxs-lookup"><span data-stu-id="d9ad7-117">Access to the members of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="d9ad7-118">新增 `Imports` 陳述式 (如果未在程式碼中完整限定成員名稱)。</span><span class="sxs-lookup"><span data-stu-id="d9ad7-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="d9ad7-119">如需詳細資訊，請參閱 [Imports 陳述式 (.NET 命名空間和類型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。</span><span class="sxs-lookup"><span data-stu-id="d9ad7-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="d9ad7-120">安全性</span><span class="sxs-lookup"><span data-stu-id="d9ad7-120">Security</span></span>  
 <span data-ttu-id="d9ad7-121">如果您要透過網路移動密碼，您需要將資料傳輸會使用安全的方法。</span><span class="sxs-lookup"><span data-stu-id="d9ad7-121">If you are moving the password across a network, you need to use a secure method for transferring data.</span></span> <span data-ttu-id="d9ad7-122">如需詳細資訊，請參閱[ASP.NET Web 應用程式安全性](https://msdn.microsoft.com/library/330a99hc)。</span><span class="sxs-lookup"><span data-stu-id="d9ad7-122">For more information, see [ASP.NET Web Application Security](https://msdn.microsoft.com/library/330a99hc).</span></span>  
  
 <span data-ttu-id="d9ad7-123">您可以改善的精確度`ValidatePassword`函式加上額外的複雜性檢查：</span><span class="sxs-lookup"><span data-stu-id="d9ad7-123">You can improve the accuracy of the `ValidatePassword` function by adding additional complexity checks:</span></span>  
  
-   <span data-ttu-id="d9ad7-124">密碼和使用者的名稱、 使用者識別碼和應用程式定義的字典針對子字串比較。</span><span class="sxs-lookup"><span data-stu-id="d9ad7-124">Compare the password and its substrings against the user's name, user identifier, and an application-defined dictionary.</span></span> <span data-ttu-id="d9ad7-125">此外，將看起來類似字元視為對等項目時執行的比較。</span><span class="sxs-lookup"><span data-stu-id="d9ad7-125">In addition, treat visually similar characters as equivalent when performing the comparisons.</span></span> <span data-ttu-id="d9ad7-126">例如，視為字母"l"和"e"等於數字"1"和"3"。</span><span class="sxs-lookup"><span data-stu-id="d9ad7-126">For example, treat the letters "l" and "e" as equivalent to the numerals "1" and "3".</span></span>  
  
-   <span data-ttu-id="d9ad7-127">如果只有一個大寫字元，請確定它不是密碼的第一個字元。</span><span class="sxs-lookup"><span data-stu-id="d9ad7-127">If there is only one uppercase character, make sure it is not the password's first character.</span></span>  
  
-   <span data-ttu-id="d9ad7-128">請確定密碼最後兩個字元的字母字元。</span><span class="sxs-lookup"><span data-stu-id="d9ad7-128">Make sure that the last two characters of the password are letter characters.</span></span>  
  
-   <span data-ttu-id="d9ad7-129">不允許輸入從鍵盤的上方資料列的所有符號的密碼。</span><span class="sxs-lookup"><span data-stu-id="d9ad7-129">Do not allow passwords in which all the symbols are entered from the keyboard's top row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9ad7-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9ad7-130">See Also</span></span>  
 <xref:System.Text.RegularExpressions.Regex>  
 [<span data-ttu-id="d9ad7-131">ASP.NET Web 應用程式安全性</span><span class="sxs-lookup"><span data-stu-id="d9ad7-131">ASP.NET Web Application Security</span></span>](https://msdn.microsoft.com/library/330a99hc)
