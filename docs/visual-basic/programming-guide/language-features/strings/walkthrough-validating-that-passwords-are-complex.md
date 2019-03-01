---
title: 驗證密碼複雜性 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: fb95871f347bf1093701a428a8b925f884d17a56
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979693"
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a><span data-ttu-id="37dcb-102">逐步解說：驗證密碼確實複雜 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37dcb-102">Walkthrough: Validating That Passwords Are Complex (Visual Basic)</span></span>
<span data-ttu-id="37dcb-103">這個方法會檢查一些強式密碼的特性，並以了解哪種檢查密碼失敗的資訊更新字串參數。</span><span class="sxs-lookup"><span data-stu-id="37dcb-103">This method checks for some strong-password characteristics and updates a string parameter with information about which checks the password fails.</span></span>  
  
 <span data-ttu-id="37dcb-104">密碼可以用在安全的系統，來授權使用者。</span><span class="sxs-lookup"><span data-stu-id="37dcb-104">Passwords can be used in a secure system to authorize a user.</span></span> <span data-ttu-id="37dcb-105">不過，密碼必須很難猜出未經授權的使用者。</span><span class="sxs-lookup"><span data-stu-id="37dcb-105">However, the passwords must be difficult for unauthorized users to guess.</span></span> <span data-ttu-id="37dcb-106">攻擊者可以使用*字典攻擊*的程式，可逐一查看所有字典 （或不同的語言中的多個字典） 中的文字，並測試是否有任何文字做為使用者的密碼。</span><span class="sxs-lookup"><span data-stu-id="37dcb-106">Attackers can use a *dictionary attack* program, which iterates through all of the words in a dictionary (or multiple dictionaries in different languages) and tests whether any of the words work as a user's password.</span></span> <span data-ttu-id="37dcb-107">弱式密碼，例如"洋基隊 」 或 「 Mustang 」 可以快速地猜到。</span><span class="sxs-lookup"><span data-stu-id="37dcb-107">Weak passwords such as "Yankees" or "Mustang" can be guessed quickly.</span></span> <span data-ttu-id="37dcb-108">強式密碼，例如"？您 'L1N3vaFiNdMeyeP@sSWerd！ 」，比較不容易猜到。</span><span class="sxs-lookup"><span data-stu-id="37dcb-108">Stronger passwords, such as "?You'L1N3vaFiNdMeyeP@sSWerd!", are much less likely to be guessed.</span></span> <span data-ttu-id="37dcb-109">受密碼保護的系統應該確保使用者選擇強式密碼。</span><span class="sxs-lookup"><span data-stu-id="37dcb-109">A password-protected system should ensure that users choose strong passwords.</span></span>  
  
 <span data-ttu-id="37dcb-110">強式密碼很複雜 （包含大寫、 小寫、 數字和特殊字元的混合），而且不是一個字。</span><span class="sxs-lookup"><span data-stu-id="37dcb-110">A strong password is complex (containing a mixture of uppercase, lowercase, numeric, and special characters) and is not a word.</span></span> <span data-ttu-id="37dcb-111">此範例示範如何驗證複雜性。</span><span class="sxs-lookup"><span data-stu-id="37dcb-111">This example demonstrates how to verify complexity.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37dcb-112">範例</span><span class="sxs-lookup"><span data-stu-id="37dcb-112">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="37dcb-113">程式碼</span><span class="sxs-lookup"><span data-stu-id="37dcb-113">Code</span></span>  
 [!code-vb[VbVbcnRegEx#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="37dcb-114">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="37dcb-114">Compiling the Code</span></span>  
 <span data-ttu-id="37dcb-115">呼叫這個方法，傳遞包含該密碼的字串。</span><span class="sxs-lookup"><span data-stu-id="37dcb-115">Call this method by passing the string that contains that password.</span></span>  
  
 <span data-ttu-id="37dcb-116">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="37dcb-116">This example requires:</span></span>  
  
-   <span data-ttu-id="37dcb-117"><xref:System.Text.RegularExpressions> 命名空間成員的存取權。</span><span class="sxs-lookup"><span data-stu-id="37dcb-117">Access to the members of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="37dcb-118">新增 `Imports` 陳述式 (如果未在程式碼中完整限定成員名稱)。</span><span class="sxs-lookup"><span data-stu-id="37dcb-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="37dcb-119">如需詳細資訊，請參閱 [Imports 陳述式 (.NET 命名空間和類型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。</span><span class="sxs-lookup"><span data-stu-id="37dcb-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="37dcb-120">安全性</span><span class="sxs-lookup"><span data-stu-id="37dcb-120">Security</span></span>  
 <span data-ttu-id="37dcb-121">如果您要透過網路移動的密碼，您需要將資料傳輸會使用安全的方法。</span><span class="sxs-lookup"><span data-stu-id="37dcb-121">If you're moving the password across a network, you need to use a secure method for transferring data.</span></span> <span data-ttu-id="37dcb-122">如需詳細資訊，請參閱 < [ASP.NET Web 應用程式安全性](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="37dcb-122">For more information, see [ASP.NET Web Application Security](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100)).</span></span>
  
 <span data-ttu-id="37dcb-123">您可以改善的精確度`ValidatePassword`加上額外的複雜性檢查函式：</span><span class="sxs-lookup"><span data-stu-id="37dcb-123">You can improve the accuracy of the `ValidatePassword` function by adding additional complexity checks:</span></span>  
  
-   <span data-ttu-id="37dcb-124">密碼和使用者的名稱、 使用者識別碼和應用程式定義的字典的子字串比較。</span><span class="sxs-lookup"><span data-stu-id="37dcb-124">Compare the password and its substrings against the user's name, user identifier, and an application-defined dictionary.</span></span> <span data-ttu-id="37dcb-125">執行比較時，此外，將視為對等項目看起來類似的字元。</span><span class="sxs-lookup"><span data-stu-id="37dcb-125">In addition, treat visually similar characters as equivalent when performing the comparisons.</span></span> <span data-ttu-id="37dcb-126">比方說，視為字母"l"和"e"等於"1"和"3"的數字。</span><span class="sxs-lookup"><span data-stu-id="37dcb-126">For example, treat the letters "l" and "e" as equivalent to the numerals "1" and "3".</span></span>  
  
-   <span data-ttu-id="37dcb-127">如果只有一個大寫字元，請確定它不是密碼的第一個字元。</span><span class="sxs-lookup"><span data-stu-id="37dcb-127">If there is only one uppercase character, make sure it is not the password's first character.</span></span>  
  
-   <span data-ttu-id="37dcb-128">請確定密碼的最後兩個字元的字母字元。</span><span class="sxs-lookup"><span data-stu-id="37dcb-128">Make sure that the last two characters of the password are letter characters.</span></span>  
  
-   <span data-ttu-id="37dcb-129">不允許在其中從鍵盤上方資料列輸入所有符號的密碼。</span><span class="sxs-lookup"><span data-stu-id="37dcb-129">Do not allow passwords in which all the symbols are entered from the keyboard's top row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37dcb-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37dcb-130">See also</span></span>
- <xref:System.Text.RegularExpressions.Regex>
- <span data-ttu-id="37dcb-131">[ASP.NET Web 應用程式安全性](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="37dcb-131">[ASP.NET Web Application Security](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))</span></span>
