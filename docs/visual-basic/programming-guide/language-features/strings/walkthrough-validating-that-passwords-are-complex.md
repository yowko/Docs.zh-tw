---
title: 驗證密碼複雜性
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: 6e8697379a6fbb5cc15b60291e5b822897c2c013
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348333"
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a><span data-ttu-id="c4d5d-102">逐步解說：驗證密碼確實複雜 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4d5d-102">Walkthrough: Validating That Passwords Are Complex (Visual Basic)</span></span>
<span data-ttu-id="c4d5d-103">這個方法會檢查是否有一些強式密碼特性，並使用檢查密碼失敗的相關資訊來更新字串參數。</span><span class="sxs-lookup"><span data-stu-id="c4d5d-103">This method checks for some strong-password characteristics and updates a string parameter with information about which checks the password fails.</span></span>  
  
 <span data-ttu-id="c4d5d-104">密碼可以在安全的系統中用來授權使用者。</span><span class="sxs-lookup"><span data-stu-id="c4d5d-104">Passwords can be used in a secure system to authorize a user.</span></span> <span data-ttu-id="c4d5d-105">不過，未經授權的使用者可能不容易猜到密碼。</span><span class="sxs-lookup"><span data-stu-id="c4d5d-105">However, the passwords must be difficult for unauthorized users to guess.</span></span> <span data-ttu-id="c4d5d-106">攻擊者可以使用*字典攻擊*程式，逐一查看字典中的所有單字（或不同語言的多個字典），並測試任何單字是否做為使用者的密碼。</span><span class="sxs-lookup"><span data-stu-id="c4d5d-106">Attackers can use a *dictionary attack* program, which iterates through all of the words in a dictionary (or multiple dictionaries in different languages) and tests whether any of the words work as a user's password.</span></span> <span data-ttu-id="c4d5d-107">弱式密碼（例如 "洋基隊" 或 "Mustang"）可能很快就會被猜到。</span><span class="sxs-lookup"><span data-stu-id="c4d5d-107">Weak passwords such as "Yankees" or "Mustang" can be guessed quickly.</span></span> <span data-ttu-id="c4d5d-108">更強的密碼，例如「？您的「L1N3vaFiNdMeyeP@sSWerd！」很少被猜到。</span><span class="sxs-lookup"><span data-stu-id="c4d5d-108">Stronger passwords, such as "?You'L1N3vaFiNdMeyeP@sSWerd!", are much less likely to be guessed.</span></span> <span data-ttu-id="c4d5d-109">受密碼保護的系統應確保使用者選擇強式密碼。</span><span class="sxs-lookup"><span data-stu-id="c4d5d-109">A password-protected system should ensure that users choose strong passwords.</span></span>  
  
 <span data-ttu-id="c4d5d-110">強式密碼很複雜（包含大寫、小寫、數位和特殊字元的混合），而且不是單字。</span><span class="sxs-lookup"><span data-stu-id="c4d5d-110">A strong password is complex (containing a mixture of uppercase, lowercase, numeric, and special characters) and is not a word.</span></span> <span data-ttu-id="c4d5d-111">這個範例會示範如何驗證複雜度。</span><span class="sxs-lookup"><span data-stu-id="c4d5d-111">This example demonstrates how to verify complexity.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4d5d-112">範例</span><span class="sxs-lookup"><span data-stu-id="c4d5d-112">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="c4d5d-113">程式碼</span><span class="sxs-lookup"><span data-stu-id="c4d5d-113">Code</span></span>  
 [!code-vb[VbVbcnRegEx#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c4d5d-114">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="c4d5d-114">Compiling the Code</span></span>  
 <span data-ttu-id="c4d5d-115">藉由傳遞包含該密碼的字串來呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="c4d5d-115">Call this method by passing the string that contains that password.</span></span>  
  
 <span data-ttu-id="c4d5d-116">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="c4d5d-116">This example requires:</span></span>  
  
- <span data-ttu-id="c4d5d-117"><xref:System.Text.RegularExpressions> 命名空間成員的存取權。</span><span class="sxs-lookup"><span data-stu-id="c4d5d-117">Access to the members of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="c4d5d-118">新增 `Imports` 陳述式 (如果未在程式碼中完整限定成員名稱)。</span><span class="sxs-lookup"><span data-stu-id="c4d5d-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="c4d5d-119">如需詳細資訊，請參閱 [Imports 陳述式 (.NET 命名空間和類型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。</span><span class="sxs-lookup"><span data-stu-id="c4d5d-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="c4d5d-120">安全性</span><span class="sxs-lookup"><span data-stu-id="c4d5d-120">Security</span></span>  
 <span data-ttu-id="c4d5d-121">如果您要在網路上移動密碼，則需要使用安全的方法來傳輸資料。</span><span class="sxs-lookup"><span data-stu-id="c4d5d-121">If you're moving the password across a network, you need to use a secure method for transferring data.</span></span> <span data-ttu-id="c4d5d-122">如需詳細資訊，請參閱[ASP.NET Web 應用程式安全性](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="c4d5d-122">For more information, see [ASP.NET Web Application Security](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100)).</span></span>
  
 <span data-ttu-id="c4d5d-123">您可以藉由新增額外的複雜性檢查，來改善 `ValidatePassword` 函式的精確度：</span><span class="sxs-lookup"><span data-stu-id="c4d5d-123">You can improve the accuracy of the `ValidatePassword` function by adding additional complexity checks:</span></span>  
  
- <span data-ttu-id="c4d5d-124">根據使用者的名稱、使用者識別碼和應用程式定義的字典來比較密碼和子字串。</span><span class="sxs-lookup"><span data-stu-id="c4d5d-124">Compare the password and its substrings against the user's name, user identifier, and an application-defined dictionary.</span></span> <span data-ttu-id="c4d5d-125">此外，執行比較時，將視覺效果相似的字元視為對等。</span><span class="sxs-lookup"><span data-stu-id="c4d5d-125">In addition, treat visually similar characters as equivalent when performing the comparisons.</span></span> <span data-ttu-id="c4d5d-126">例如，將字母 "l" 和 "e" 視為等於數位 "1" 和 "3"。</span><span class="sxs-lookup"><span data-stu-id="c4d5d-126">For example, treat the letters "l" and "e" as equivalent to the numerals "1" and "3".</span></span>  
  
- <span data-ttu-id="c4d5d-127">如果只有一個大寫字元，請確定它不是密碼的第一個字元。</span><span class="sxs-lookup"><span data-stu-id="c4d5d-127">If there is only one uppercase character, make sure it is not the password's first character.</span></span>  
  
- <span data-ttu-id="c4d5d-128">請確定密碼的最後兩個字元是字母字元。</span><span class="sxs-lookup"><span data-stu-id="c4d5d-128">Make sure that the last two characters of the password are letter characters.</span></span>  
  
- <span data-ttu-id="c4d5d-129">不允許從鍵盤頂端資料列輸入所有符號的密碼。</span><span class="sxs-lookup"><span data-stu-id="c4d5d-129">Do not allow passwords in which all the symbols are entered from the keyboard's top row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4d5d-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="c4d5d-130">See also</span></span>

- <xref:System.Text.RegularExpressions.Regex>
- <span data-ttu-id="c4d5d-131">[ASP.NET Web 應用程式安全性](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c4d5d-131">[ASP.NET Web Application Security](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))</span></span>
