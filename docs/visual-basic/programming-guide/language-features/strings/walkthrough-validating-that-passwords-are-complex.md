---
title: "驗證密碼複雜性 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- String data type, validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
caps.latest.revision: 17
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
ms.openlocfilehash: 8d636c1e43de6a108cdc217cb21aaf7689e175f7
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a><span data-ttu-id="102eb-102">逐步解說：驗證密碼確實複雜 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="102eb-102">Walkthrough: Validating That Passwords Are Complex (Visual Basic)</span></span>
<span data-ttu-id="102eb-103">這個方法會檢查有部份特性的強式密碼，並更新字串參數的檢查密碼失敗的資訊。</span><span class="sxs-lookup"><span data-stu-id="102eb-103">This method checks for some strong-password characteristics and updates a string parameter with information about which checks the password fails.</span></span>  
  
 <span data-ttu-id="102eb-104">密碼可以用在安全的系統，來授權使用者。</span><span class="sxs-lookup"><span data-stu-id="102eb-104">Passwords can be used in a secure system to authorize a user.</span></span> <span data-ttu-id="102eb-105">不過，密碼必須是難猜出未經授權的使用者。</span><span class="sxs-lookup"><span data-stu-id="102eb-105">However, the passwords must be difficult for unauthorized users to guess.</span></span> <span data-ttu-id="102eb-106">攻擊者可以使用*字典攻擊*的程式，可逐一查看所有字典 （或多個字典，以不同的語言） 中的字數，並測試是否有任何文字做為使用者的密碼。</span><span class="sxs-lookup"><span data-stu-id="102eb-106">Attackers can use a *dictionary attack* program, which iterates through all of the words in a dictionary (or multiple dictionaries in different languages) and tests whether any of the words work as a user's password.</span></span> <span data-ttu-id="102eb-107">弱式密碼，例如 「 洋基 」 或 「 Mustang 」 可以快速地猜到了。</span><span class="sxs-lookup"><span data-stu-id="102eb-107">Weak passwords such as "Yankees" or "Mustang" can be guessed quickly.</span></span> <span data-ttu-id="102eb-108">更嚴密的密碼，例如"嗎？您 'L1N3vaFiNdMeyeP@sSWerd！ 」，更不容易猜到。</span><span class="sxs-lookup"><span data-stu-id="102eb-108">Stronger passwords, such as "?You'L1N3vaFiNdMeyeP@sSWerd!", are much less likely to be guessed.</span></span> <span data-ttu-id="102eb-109">密碼保護的系統應該確定使用者選擇強式密碼。</span><span class="sxs-lookup"><span data-stu-id="102eb-109">A password-protected system should ensure that users choose strong passwords.</span></span>  
  
 <span data-ttu-id="102eb-110">強式密碼很複雜 （包含大寫、 小寫、 數字和特殊字元的混合），而且不是字。</span><span class="sxs-lookup"><span data-stu-id="102eb-110">A strong password is complex (containing a mixture of uppercase, lowercase, numeric, and special characters) and is not a word.</span></span> <span data-ttu-id="102eb-111">這個範例示範如何驗證複雜度。</span><span class="sxs-lookup"><span data-stu-id="102eb-111">This example demonstrates how to verify complexity.</span></span>  
  
## <a name="example"></a><span data-ttu-id="102eb-112">範例</span><span class="sxs-lookup"><span data-stu-id="102eb-112">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="102eb-113">程式碼</span><span class="sxs-lookup"><span data-stu-id="102eb-113">Code</span></span>  
 <span data-ttu-id="102eb-114">[!code-vb[VbVbcnRegEx #&1;](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/walkthrough-validating-that-passwords-are-complex_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="102eb-114">[!code-vb[VbVbcnRegEx#1](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/walkthrough-validating-that-passwords-are-complex_1.vb)]</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="102eb-115">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="102eb-115">Compiling the Code</span></span>  
 <span data-ttu-id="102eb-116">呼叫這個方法，傳遞包含該密碼的字串。</span><span class="sxs-lookup"><span data-stu-id="102eb-116">Call this method by passing the string that contains that password.</span></span>  
  
 <span data-ttu-id="102eb-117">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="102eb-117">This example requires:</span></span>  
  
-   <span data-ttu-id="102eb-118">存取的成員<xref:System.Text.RegularExpressions>命名空間。</xref:System.Text.RegularExpressions></span><span class="sxs-lookup"><span data-stu-id="102eb-118">Access to the members of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="102eb-119">新增`Imports`陳述式，如果您不完整限定成員名稱在您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="102eb-119">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="102eb-120">如需詳細資訊，請參閱 [Imports 陳述式 (.NET 命名空間和類型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。</span><span class="sxs-lookup"><span data-stu-id="102eb-120">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="102eb-121">安全性</span><span class="sxs-lookup"><span data-stu-id="102eb-121">Security</span></span>  
 <span data-ttu-id="102eb-122">如果您要透過網路移動密碼，您需要使用安全的方法來傳送資料。</span><span class="sxs-lookup"><span data-stu-id="102eb-122">If you are moving the password across a network, you need to use a secure method for transferring data.</span></span> <span data-ttu-id="102eb-123">如需詳細資訊，請參閱[ASP.NET Web 應用程式安全性](https://msdn.microsoft.com/library/330a99hc)。</span><span class="sxs-lookup"><span data-stu-id="102eb-123">For more information, see [ASP.NET Web Application Security](https://msdn.microsoft.com/library/330a99hc).</span></span>  
  
 <span data-ttu-id="102eb-124">您可以改善的精確度`ValidatePassword`藉由新增額外的複雜性檢查函式︰</span><span class="sxs-lookup"><span data-stu-id="102eb-124">You can improve the accuracy of the `ValidatePassword` function by adding additional complexity checks:</span></span>  
  
-   <span data-ttu-id="102eb-125">密碼和使用者的名稱、 使用者識別碼和應用程式定義的字典的子字串比較。</span><span class="sxs-lookup"><span data-stu-id="102eb-125">Compare the password and its substrings against the user's name, user identifier, and an application-defined dictionary.</span></span> <span data-ttu-id="102eb-126">執行比較時，此外，將視為對等項目看起來類似的字元。</span><span class="sxs-lookup"><span data-stu-id="102eb-126">In addition, treat visually similar characters as equivalent when performing the comparisons.</span></span> <span data-ttu-id="102eb-127">例如，視為字母"l"和"e"等於"1"和"3"的數字。</span><span class="sxs-lookup"><span data-stu-id="102eb-127">For example, treat the letters "l" and "e" as equivalent to the numerals "1" and "3".</span></span>  
  
-   <span data-ttu-id="102eb-128">如果只有一個大寫字元，請確定它不是密碼的第一個字元。</span><span class="sxs-lookup"><span data-stu-id="102eb-128">If there is only one uppercase character, make sure it is not the password's first character.</span></span>  
  
-   <span data-ttu-id="102eb-129">請確定密碼的最後兩個字元的字母字元。</span><span class="sxs-lookup"><span data-stu-id="102eb-129">Make sure that the last two characters of the password are letter characters.</span></span>  
  
-   <span data-ttu-id="102eb-130">不允許輸入從鍵盤的上方資料列的所有符號的密碼。</span><span class="sxs-lookup"><span data-stu-id="102eb-130">Do not allow passwords in which all the symbols are entered from the keyboard's top row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="102eb-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="102eb-131">See Also</span></span>  
 <span data-ttu-id="102eb-132"><xref:System.Text.RegularExpressions.Regex></xref:System.Text.RegularExpressions.Regex></span><span class="sxs-lookup"><span data-stu-id="102eb-132"><xref:System.Text.RegularExpressions.Regex></span></span>   
<span data-ttu-id="102eb-133"> [ASP.NET Web 應用程式安全性](https://msdn.microsoft.com/library/330a99hc)</span><span class="sxs-lookup"><span data-stu-id="102eb-133"> [ASP.NET Web Application Security](https://msdn.microsoft.com/library/330a99hc)</span></span>
